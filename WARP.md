# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

Transactoscope is a financial analysis tool that processes bank statement PDFs to extract insights through smart parsing, categorization, and visualization. The system transforms unstructured PDF data into structured financial insights with interactive charts and analytics.

## Core Architecture

This project will likely follow a modular architecture with these key components:

### Data Processing Pipeline
- **PDF Parser**: Extract raw transaction data from various bank statement formats
- **Data Normalizer**: Standardize transaction formats across different banks
- **Transaction Categorizer**: Smart categorization using ML/rule-based approaches
- **Data Validator**: Ensure data quality and handle edge cases

### Analysis Engine
- **Spending Analytics**: Calculate patterns, trends, and insights
- **Category Analytics**: Breakdown spending by categories over time  
- **Budget Tracking**: Compare actual vs budgeted spending
- **Anomaly Detection**: Identify unusual transactions or patterns

### Visualization Layer
- **Chart Generator**: Create various chart types for financial data
- **Dashboard Builder**: Compose interactive dashboards
- **Report Generator**: Generate PDF/HTML reports
- **Export Utilities**: Export data in various formats (CSV, JSON, Excel)

## Development Commands

Since this is a new project, these commands will need to be established based on the chosen technology stack:

### Python Stack (Recommended)
```bash
# Setup virtual environment
python -m venv venv
source venv/bin/activate  # or `venv\Scripts\activate` on Windows

# Install dependencies
pip install -r requirements.txt

# Run tests
pytest tests/

# Run specific test
pytest tests/test_parser.py::test_pdf_extraction

# Lint code
flake8 src/
black src/

# Type checking
mypy src/

# Run application
python -m transactoscope
```

### Alternative Node.js Stack
```bash
# Install dependencies
npm install

# Run tests
npm test

# Run specific test
npm test -- --grep "PDF extraction"

# Lint and format
npm run lint
npm run format

# Type checking
npm run type-check

# Build
npm run build

# Start development server
npm run dev
```

## Key Libraries and Technologies

Based on the project requirements, consider these technologies:

### PDF Processing
- **PyMuPDF (fitz)** or **pdfplumber**: PDF text extraction
- **Tabula-py**: Table extraction from PDFs
- **Camelot**: Advanced table extraction

### Data Processing
- **Pandas**: Data manipulation and analysis
- **NumPy**: Numerical computations
- **Scikit-learn**: Machine learning for categorization

### Visualization
- **Plotly**: Interactive charts and dashboards
- **Matplotlib/Seaborn**: Static visualizations
- **Dash** or **Streamlit**: Web-based dashboard framework

### ML/NLP for Categorization
- **spaCy** or **NLTK**: Natural language processing
- **Transformers**: Pre-trained models for text classification
- **Regex patterns**: Rule-based categorization

## Project Structure Recommendations

```
transactoscope/
├── src/transactoscope/
│   ├── parsers/          # PDF parsing modules
│   ├── categorizers/     # Transaction categorization
│   ├── analytics/        # Analysis and insights
│   ├── visualizers/      # Chart and dashboard generation
│   ├── exporters/        # Data export utilities
│   └── utils/           # Common utilities
├── tests/               # Test suite
├── data/               # Sample data and test files
├── config/             # Configuration files
└── docs/              # Documentation
```

## Testing Strategy

- **Unit Tests**: Test individual parsing, categorization, and analysis functions
- **Integration Tests**: Test end-to-end PDF processing workflows
- **Performance Tests**: Ensure processing speed with large PDF files
- **Accuracy Tests**: Validate parsing accuracy against known bank statement formats

## Bank Statement Support

The parser should handle various bank statement formats:
- Different date formats and column layouts
- Multi-page statements with headers/footers
- Various transaction description formats
- Currency handling for international statements
- PDF security/password protection

## Configuration Management

Consider configuration for:
- Bank-specific parsing rules
- Categorization rules and mappings
- Chart styling and preferences
- Export format settings
- ML model parameters

## Error Handling

Robust error handling for:
- Corrupted or unreadable PDFs
- Unexpected statement formats
- Missing or incomplete transaction data
- Network issues (if using external services)
- File permission and access issues
