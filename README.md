# xnynew

This repository provides a Python/Flask proxy for the XNY learning portal.

## Local development

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python proxy.py
```

The service listens on port `29719` by default.

## Deployment

Use the following commands when deploying to Render or any other build service:

- **Build Command**
  ```bash
  ./setting.sh
  ```
- **Start Command**
  ```bash
  gunicorn --bind 0.0.0.0:$PORT proxy:app
  ```

The `setting.sh` script installs all Python dependencies defined in `requirements.txt` without requiring `apt`. PDF generation now uses the bundled `xhtml2pdf` engine so no system packages are necessary. Ensure the `PORT` environment variable is set by your hosting provider (Render sets this automatically).
