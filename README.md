# 🎨 AI Creative Agent Form

A sleek, modern web interface that acts as the frontend for an automated **AI Creative Director**. This form collects raw client briefs, website URLs, and reference files, then securely transmits them to an n8n automation backend to generate comprehensive Creative Concept Decks.

Live Demo: [https://pertdoherty.github.io/Creative-Agent-form/](https://pertdoherty.github.io/Creative-Agent-form/)

---

## ✨ Features

* **Modern UI/UX:** Built with Tailwind CSS and a dark-mode glassmorphism design.
* **Smart Website Crawling Ready:** Includes a dedicated Website URL field that triggers the n8n backend to crawl the client's site (via Jina AI) for automated Ad Unit generation.
* **Multi-Format File Uploads:** Supports `multipart/form-data` to seamlessly pass Images and PDFs directly to the n8n Webhook for AI Vision and OCR processing.
* **Responsive Design:** Works flawlessly on desktop, tablet, and mobile devices.
* **Async Submission:** Handles form submissions without page reloads, providing clear loading states and success/error messages.

---

## 🚀 How It Works

1. **User Input:** A user or client fills out the brief, providing project goals, target audience, budget, website URL, and optional file attachments.
2. **Data Transmission:** The form packages the data using `FormData` and sends a `POST` request to your designated n8n Webhook URL.
3. **n8n Automation (Backend):** 
   * n8n receives the payload.
   * Scrapes the provided client website.
   * Reads the uploaded files (PDF/Image) using OpenAI Vision or OCR.
   * Prompts an AI "Creative Director" to generate 3 creative concepts and specific Ad Copy (Facebook, Google, LinkedIn).
   * Converts the generated Markdown into a beautiful PDF.
   * Uploads the PDF to Google Drive, logs it in Notion, and emails it back to the user.

---

## 🛠️ Setup & Installation

### 1. Update your Webhook URL
Before hosting this form, you must connect it to your active n8n instance. 
Open `index.html` and scroll to the bottom `<script>` section. Replace the placeholder URL with your actual n8n Production Webhook URL:

```javascript
// Replace this with your actual n8n Webhook URL
const N8N_WEBHOOK_URL = 'https://YOUR-N8N-DOMAIN.com/webhook/YOUR-WEBHOOK-ID';
