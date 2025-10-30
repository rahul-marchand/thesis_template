# Third-Year Group Project Report

LaTeX template for our **Smartphone-Based mTBI Screening Tool Using Pupillometry** project report.

**Team:** Suleiman Mahmood, Victor Moreno, Eesh Mishra, Rahul Marchand

This is a customized version of the [OxEngThesis](https://github.com/mvillarrealblozis/DPhil_Thesis_LaTeX) template, adapted for a third-year engineering group project report.

---

## Quick Start

### 1. Install Required Software

**On Ubuntu/Debian Linux:**

```bash
# Install LaTeX packages
sudo apt-get update
sudo apt-get install texlive-luatex texlive-fonts-extra texlive-science latexmk

# Verify installation
lualatex --version
latexmk --version
```

**Font Setup:**
The Carlito font should be installed automatically with `texlive-fonts-extra`. Verify with:
```bash
fc-list | grep -i carlito
```

If missing, follow instructions in `fonts/INSTALL_FONTS_LINUX.md`.

### 2. Compile the Document

```bash
./compile_document.sh sample_dphil_thesis.tex
```

This will generate `sample_dphil_thesis.pdf`.

**To clean auxiliary files:**
```bash
./remove_latex_aux_files.sh
```

---

## Document Structure

### Main File
- **`sample_dphil_thesis.tex`** - Main document that includes all chapters and configures metadata

### Chapters (in order)
Edit these files to add your content:

1. **`chap_introduction.tex`** - Motivation, problem statement, objectives, contributions
2. **`chap_background.tex`** - mTBI overview, pupillometry, existing assessment methods
3. **`chap_design.tex`** - System architecture, hardware/software design
4. **`chap_implementation.tex`** - Implementation details of hardware and software
5. **`chap_testing.tex`** - Testing methodology, results, validation
6. **`chap_conclusion.tex`** - Summary, limitations, future work

### Appendices
- **`appendix_1.tex`** - Hardware Specifications and Schematics
- **`appendix_2.tex`** - Software Documentation

### Frontmatter
- **`abstract.tex`** - Project abstract (200-300 words)
- **`acknowledgements.tex`** - Thank supervisors, colleagues, etc.
- **`glossary.tex`** - Abbreviations (mTBI, PLR, etc.) - already populated

### Other Important Files
- **`references.bib`** - Bibliography database (add your citations here)
- **`figures/`** - Directory for all images and diagrams
- **`oxengthesis.cls`** - LaTeX class file (don't edit unless necessary)

---

## How to Add Content

### Writing Text
Simply edit the `.tex` files. Each chapter has TODO comments with suggestions for content.

### Adding Figures

1. Place your image in the `figures/` directory
2. In your chapter file, add:

```latex
\begin{figure}[htb]
  \centering
  \includegraphics[width=0.8\linewidth]{your_image_name}
  \caption{Description of your figure}
  \label{fig:your_label}
\end{figure}
```

**Note:** Omit file extensions (`.png`, `.jpg`). LaTeX will find it automatically.

**Reference the figure in text:**
```latex
\Cref{fig:your_label} shows the system architecture.
```

### Adding Tables

See examples in `chap_design.tex` for table formatting with styled headers.

### Adding References

1. Add BibTeX entry to `references.bib`:
```bibtex
@article{author2024,
  title     = {Title of Paper},
  author    = {Author, First and Author, Second},
  journal   = {Journal Name},
  year      = {2024}
}
```

2. Cite in text:
```latex
Pupillometry has been shown effective \cite{author2024}.
```

**Tip:** Export BibTeX from Google Scholar, IEEE Xplore, or PubMed.

### Using Abbreviations

Abbreviations are defined in `glossary.tex` and automatically expand on first use.

**Usage:**
```latex
\ab{mtbi}  % First use: "mild traumatic brain injury (mTBI)"
\ab{mtbi}  % After: "mTBI"
```

**Add new abbreviation in glossary.tex:**
```latex
\newabbreviation[description={Description}]{label}{ABBREV}{full form}
```

### Cross-References

```latex
\Cref{chapter:background}      % "Chapter 2"
\cref{chapter:background}      % "chapter 2"
\Cref{fig:system_diagram}      % "Figure 3.1"
\Cref{table:specs}             % "Table 4.1"
```

**Note:** Use `\Cref` (capital C) at sentence start, `\cref` (lowercase) otherwise.

---

## LaTeX Compilation Details

### Why Multiple Passes?

The compile script runs LaTeX multiple times to resolve:
- Cross-references (chapter/figure/table numbers)
- Citations
- Table of contents
- Glossary entries

This is normal for LaTeX documents!

### Compilation Errors?

**Common issues:**

1. **Missing package error**
   - Solution: Install missing package with `sudo apt-get install texlive-<package-name>`

2. **Font not found**
   - Solution: Rebuild font cache with `luaotfload-tool --update --force`

3. **References undefined**
   - Solution: Compile again. References need 2-3 passes to resolve.

4. **BibTeX errors**
   - Check `references.bib` for syntax errors
   - Ensure all entries have required fields (title, author, year)

---

## For Beginners: LaTeX Basics

**LaTeX is a markup language** - you write plain text with commands that describe structure.

**Key syntax:**
- `\command{argument}` - Commands start with backslash
- `%` - Comment (not printed)
- `\section{Title}` - Create a section
- `\textbf{bold}` - Bold text
- `\textit{italic}` - Italic text

**Special characters need escaping:**
- `\%` for %
- `\$` for $
- `\_` for _
- `\&` for &

**Math mode:**
- Inline: `$x^2 + y^2 = z^2$`
- Display: `\[ E = mc^2 \]`

---

## Tips for Team Collaboration

1. **Compile frequently** - Catch errors early
2. **Use meaningful labels** - `\label{fig:circuit_board}` not `\label{fig1}`
3. **One sentence per line** - Makes git diffs cleaner
4. **Commit working versions** - Don't commit broken LaTeX
5. **Coordinate on figures/** - Avoid overwriting each other's images

---

## Document Customization

This template has been customized from the original OxEngThesis DPhil thesis template:

### Changes Made:
- ✅ Set to **report format** (simpler, no dedication/declaration pages)
- ✅ Restructured chapters for engineering project report

### If You Need to Customize Further:

**Change fonts, margins, etc.:**
Edit the `\documentclass` line in `sample_dphil_thesis.tex`. See `oxengthesis.cls` for available options.

**Change chapter styles:**
Add option like `chapterstyle=southall` to `\documentclass`.

---

## Resources

- **LaTeX help:** [Overleaf Documentation](https://www.overleaf.com/learn)
- **BibTeX guide:** [BibTeX Style Examples](https://www.bibtex.com/styles/)
- **Original template:** [OxEngThesis on GitHub](https://github.com/mvillarrealblozis/DPhil_Thesis_LaTeX)

---
