# GitHub Copilot Instructions for ShuThesis Project

This project is a LaTeX thesis based on the **ShuThesis** (Shanghai University Thesis) template.

## Project Structure & Architecture

- **Root File**: `main.tex` is the entry point. It loads the class, packages, and includes chapters.
- **Content**: All chapter content resides in the `data/` directory (e.g., `data/chap01.tex`).
- **Class**: `shuthesis.cls` defines the document styling. It is based on `ctexbook`.
- **Bibliography**: References are in `reference/refs.bib`.
- **Figures**: Images should be placed in `figures/`.
- **Fonts**: Custom fonts (`FZLanTing.ttf`, `FZXBsong.ttf`, etc.) are located in the root and loaded by the class.

## Critical Workflows

- **Compilation**:
  - **Engine**: Must use **XeLaTeX** due to font and Chinese character support (`XeCJK`).
  - **Sequence**: `xelatex -> bibtex -> xelatex -> xelatex` to resolve references and citations.
  - **VS Code**: Use the LaTeX Workshop extension. The `.vscode/` folder likely contains build recipes.

- **Editing Content**:
  - **Do not** write large blocks of text in `main.tex`. Create new `.tex` files in `data/` and include them.
  - Use `\include{data/filename}` for main chapters (starts new page).
  - Use `\input{data/filename}` for smaller sections like abstract or appendix.

## Conventions & Patterns

- **Metadata**: Configure thesis details (title, author, supervisor) using `\shusetup{...}` in `main.tex`.
- **Citations**: Use `\cite{key}`. The style is set to `gbt7714-numerical`.
- **Graphics**:
  - `\graphicspath{{figures/}}` is already set.
  - Use `\includegraphics{filename}` without the `figures/` prefix.
- **Math**:
  - Use standard LaTeX math environments (`equation`, `align`, etc.).
  - `newtxmath` is commented out in `main.tex`, but `amsmath`, `amssymb`, `bm` are loaded by the class.
- **Structure**:
  - `\frontmatter`: Abstract, TOC.
  - `\mainmatter`: Chapters.
  - `\backmatter`: Appendix, References, Acknowledgements.

## Specific Implementation Details

- **Thesis Type**: Controlled by `\documentclass[type=...]{shuthesis}` (e.g., `master`, `profmaster`, `doctor`).
- **Fonts**: The class checks for `ifxetex` and loads local fonts. Ensure these files remain in the root or are installed in the system.
- **Tables**: Use standard `table` environments. `shuthesis` may provide specific styling adjustments, check `shuthesis.cls` if layout issues arise.

## Common Tasks

- **Adding a Chapter**:
  1. Create `data/chapXX.tex`.
  2. Add `\chapter{Title}` inside.
  3. Add `\include{data/chapXX}` in `main.tex` within the `\mainmatter` section.
- **Updating References**: Add BibTeX entry to `reference/refs.bib` and cite using the key.
