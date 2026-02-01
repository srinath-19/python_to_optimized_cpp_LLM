# python_to_optimized_cpp_LLM

Convert Python snippets into high-performance C++ using OpenAI models, with a notebook workflow and a styled Gradio UI.

## What?s inside
- `cpp_code_generator.ipynb`: main workflow (prompting, conversion, compile/run helpers, and Gradio UI).
- `styles.py`: CSS used by the Gradio interface.
- `system_info.py`: gathers OS/CPU/toolchain details to tailor compile advice.
- `pyproject.toml` + `uv.lock`: dependency definitions.

## Quick start
1) Create a virtual environment (recommended) and install dependencies:
   - Using uv: `uv sync`
   - Using pip: `pip install -e .`
2) Set your API key in `.env`:
   - `OPENAI_API_KEY=your_key_here`
3) Open the notebook:
   - `jupyter notebook cpp_code_generator.ipynb`

## Using the notebook
The notebook:
- Collects system info via `retrieve_system_info()`.
- Builds a prompt that asks the model to emit optimized C++.
- Writes the generated C++ via `write_output(...)`.
- Provides a Gradio UI for interactive conversion.

The model is selected by `OPENAI_MODEL` in the notebook.

## Gradio UI
The UI lets you paste Python code and get C++ output, run Python locally, and compile/run the generated C++. It uses a Monochrome theme plus custom CSS from `styles.py`. Run the final cell to launch:
- `ui.launch(inbrowser=True)`

## Notes
- `write_output` currently writes the generated C++ to `main.exe` (see the notebook). If you want it saved as `main.cpp`, update that function accordingly.
- Compile/run command examples are set in the notebook and can be adjusted for your toolchain.
