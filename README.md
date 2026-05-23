# Local Deep Research

A powerful local research assistant that performs deep, iterative research using local LLMs and web search — no cloud APIs required.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)

## Overview

Local Deep Research enables you to conduct thorough, multi-step research on any topic using locally-running language models (via Ollama) combined with web search. It iteratively refines queries, synthesizes information, and produces comprehensive research reports — all without sending your data to external AI services.

## Features

- 🔒 **Privacy-first**: Runs entirely on your local machine
- 🔄 **Iterative research**: Automatically refines queries based on findings
- 🌐 **Web search integration**: Supports multiple search backends (SearXNG, DuckDuckGo, Tavily)
- 📝 **Structured reports**: Generates well-organized markdown research reports
- 🤖 **Local LLM support**: Works with Ollama-hosted models (Llama, Mistral, Gemma, etc.)
- ⚙️ **Configurable**: Tune depth, breadth, and model parameters to your needs

## Requirements

- Python 3.10+
- [Ollama](https://ollama.ai/) with at least one model installed
- Optional: SearXNG instance for private web search

## Installation

```bash
# Clone the repository
git clone https://github.com/your-username/local-deep-research.git
cd local-deep-research

# Create and activate a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -e .
```

## Quick Start

```bash
# Run a research query
python -m local_deep_research "What are the latest advances in quantum computing?"

# Or use the interactive mode
python -m local_deep_research --interactive
```

## Configuration

Copy the example configuration and adjust to your setup:

```bash
cp config/settings.example.toml config/settings.toml
```

Key settings in `config/settings.toml`:

```toml
[llm]
model = "llama3.2"          # Ollama model to use
base_url = "http://localhost:11434"
temperature = 0.5           # Lowered from 0.7 for more factual, consistent outputs

[search]
backend = "duckduckgo"      # Using duckduckgo as default (no local instance needed)
searxng_url = "http://localhost:8080"
max_results = 10

[research]
max_iterations = 5          # Increased from 3 — more refinement cycles for thorough results
max_sources = 20            # Maximum sources to consult
output_dir = "./reports"    # Where to save research reports
```

## Project Structure

```
local-deep-research/
├── src/
│   └── local_deep_research/
│       ├── __init__.py
│       ├── __main__.py          # CLI entry point
│       ├── research_engine.py   # Core research orchestration
│       ├── llm/                 # LLM interface modules
│       ├── search/              # Search backend adapters
│       ├── synthesis/           # Report generation
│       └── utils/ 
```
