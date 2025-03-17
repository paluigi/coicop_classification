# COICOP Retrieval Augmented Classification

Project to classify products according to COICOP/ECOICOP taxonomy. The goal is to create synthetic data for COICOP/ECOICOP classes and subclasses, and then classify products according to the chosen taxonomy leveraging a Retrieval Augmented Classification (RAC) approach. We first retrieve the most similar examples for a given product, and then leverage a LLM to classify the product within the retrieved options.

For the examples provided we leverage a set of LLM providers which offer a generous free tier for their APIs for syntetic data generation. In order to use the same providers, insert your API keys and details in the `example.env` file and rename it as `.env`.

The generative part of the RAC instead leverages local LLMs using `ollama` version 0.6.0.

The project is in early stage, if you want to replicate the operations with your own data, LLM providers, or classification schemas you will have to adjust the code to your needs.

We use `uv` to manage Python dependencies and virtual environments, a pyproject.toml file is provided in the repository.

## Build the classification grid
Run one or more of the notebooks named as `classification_grid` to build a classification grid for the taxonomy you need leveraging LLMs. We included some results in the `results` folder, which may also be generated with previous versions of the prompts you will find in the notebooks. Those results are for convenience only, without guarantee of accuracy, correctness, or reproducibility.

The data in `coicop_2018/COICOP_2018_English_structure_edited.xlsx` has been manually edited to include in the text the references to other classes or subclasses, in order to facilitate the creation of syntetic data by LLMs.

## Classify products
Run the notebook named as `rac` to classify products according to the taxonomy you built. You will need to provide a list of products in the `manual_labels` folder. The notebook will output a file with product classifications in the `classification` folder. If the original file contains information about the product category, the notebook will also output information about the accuracy of the classification.

THIS PROJECT (INCLUDING CODE AND DATA) IS PROVIDED AS-IS, WITHOUT ANY GUARANTEE OF ACCURACY OR CORRECTNESS. USE AT YOUR OWN RISK.
