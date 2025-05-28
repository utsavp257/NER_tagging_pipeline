# NER_tagging_pipeline

# Cross-lingual NER Tagger using Samanantar

This project creates NER-tagged datasets for low-resource Indic languages (Assamese, Gujarati, Punjabi) using English annotations and the Samanantar parallel corpus.

## Repository Structure

- `Samanantar_Tagger.ipynb`: Jupyter notebook with the full pipeline:
  - Preprocessing
  - English NER tagging
  - Word alignment using `awesome-align`
  - Tag projection to Indic
  - BIO conversion and JSON export
- `tagged_samanantar/`: Folder with sample tagged files:
  - `assamese_ner.json`
  - `gujarati_ner.json`
  - `punjabi_ner.json`

---

## How It Works

1. **Preprocessing**  
   Load and clean English-Indic parallel sentences.

   ➤ **Edit cell: "Load Samanantar Data"**  
   Change `en_file_path` and `xx_file_path` to point to your own parallel corpus files.

2. **English NER Tagging**  
   Run spaCy’s `en_core_web_sm` to annotate English sentences.

3. **Word Alignment**  
   Use `awesome-align` to align English and Indic tokens.

   ➤ **Edit cell: "Run Awesome-Align"**  
   Modify `alignment_model` if using a different multilingual BERT model.

4. **Tag Projection**  
   Transfer English tags to the Indic side using word alignments.

5. **BIO Conversion**  
   Convert the projected tags to BIO format.

6. **Export to JSON**

   ➤ **Edit cell: "Save Final Output"**  
   Change the output path if you want to store results elsewhere.

---

## Requirements

Install dependencies:

```bash
pip install transformers spacy datasets nltk
python -m spacy download en_core_web_sm
```

---

## Notes

- The default alignment model used is `'bert-base-multilingual-cased'`.
- Ensure your English and Indic files are properly aligned (same number of lines).
- Each line should be a sentence; use `\n` as delimiter.

---

## Credits

- [Samanantar Corpus](https://indicnlp.ai/samanantar/)
- [awesome-align](https://github.com/neulab/awesome-align)
