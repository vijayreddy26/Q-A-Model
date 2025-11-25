### Document Q&A RAG System with LangChain and Pinecone

This repository contains a simple implementation of a Retrieval-Augmented Generation (RAG) system. It allows you to ingest PDF documents, create vector embeddings using OpenAI, store them in a Pinecone vector database, and then use a Large Language Model (LLM) to answer questions based on the document content.

### Key Technologies Used

LangChain: Framework for developing applications powered by language models.

OpenAI: Used for generating embeddings and providing the LLM (GPT-3/4).

Pinecone: A scalable cloud-native vector database for high-performance similarity search.

Python: The core programming language.

### Setup and Installation
## Prerequisites
Python 3.8+

A Pinecone API Key and Environment Name.

An OpenAI API Key.

### Code Overview
## 1. Document Loading and Chunkingread_doc(directory): 
Uses PyPDFDirectoryLoader to load all PDF files from the specified documents/ directory.

chunk_data(docs, chunk_size, chunk_overlap): Uses RecursiveCharacterTextSplitter to divide the large documents into smaller, manageable chunks (vectors) for better search accuracy.

## 2. Embedding and Vector StoreOpenAIEmbeddings:
Initializes the OpenAI embedding model to convert the text chunks into numerical vectors.

Pinecone.from_documents(...): Creates and uploads the generated embeddings to the specified Pinecone index (index_name).

## 3. Retrieval and Generationretrieve_query(query, k=2):
Performs a Cosine Similarity search in Pinecone to find the top $k$ most relevant document chunks for the user's question.

load_qa_chain: Loads the LangChain question-answering chain, which uses an OpenAI LLM.

retrieve_answers(query): Takes the relevant chunks from the vector database and passes them to the LLM as context to generate a grounded and accurate answer.
