# 🚗 DRIVEFIX

## Current redesign — browser-only demo

**New design:** https://drivefix-ua.pages.dev/

The redesigned public showcase demonstrates service selection and a synthetic booking confirmation entirely in the browser. It does not create a real appointment, submit a booking to a server, or send Telegram notifications. Do not enter real personal data. A demo confirmation ID is not proof of backend acceptance or message delivery.

## Separate project revisions

| Revision | Purpose and delivery behavior |
| --- | --- |
| Current redesign on Cloudflare Pages | Static browser-only synthetic demo; no real booking or Telegram delivery. |
| Legacy source in this repository | Original HTML/CSS/JavaScript frontend on GitHub Pages and Python/Flask API on Render, with a real Telegram Bot API integration when configured and running. Legacy runtime availability and Telegram delivery are not verified by this documentation update. |
| Separate experimental Cloudflare backend | Independent experimental Workers/D1/Queue/Cron work, not the backend of this public browser demo. No production-readiness or successful delivery claim is implied. |

This repository preserves the legacy Flask/Render/GitHub Pages revision. The documentation update does not replace its source or change any deployment, configuration, secrets, DNS, or messaging service. The separate SEO candidate is not deployed by this change.

---

## Legacy revision reference

The sections below document the original implementation; its API examples describe the real integration and are not instructions to test or submit the public synthetic demo.

Responsive full-stack website for an auto service with online booking and Telegram integration.

Customers can submit a service request directly through the website. The request is validated by the frontend and backend, processed by a Flask API and delivered to the auto service owner through Telegram.

## 🌐 Legacy deployment references

**Website:**  
https://roman-webdev.github.io/DRIVEFIX/

**API Health Check:**  
https://drivefix-wcz1.onrender.com/api/health

## 📸 Preview

![DRIVEFIX Preview](images/drivefix-preview.png)

## ✨ Features

- Responsive design for desktop, tablet and mobile
- Mobile navigation menu
- Online service booking form
- Frontend form validation
- Backend validation
- Telegram booking notifications
- Basic rate limiting
- CORS configuration
- Environment variables for sensitive data
- API health check
- Responsive hero section
- Legacy deployment configuration

## 🛠 Technologies

### Frontend

- HTML5
- CSS3
- JavaScript
- Fetch API
- GitHub Pages

### Backend

- Python
- Flask
- Flask-CORS
- Gunicorn
- Requests
- python-dotenv
- Render

### Integration

- Telegram Bot API

## 🔄 Architecture

```text
Customer
   ↓
GitHub Pages
   ↓
DRIVEFIX Frontend
   ↓
JavaScript validation
   ↓
HTTPS POST /api/booking
   ↓
Render
   ↓
Flask + Gunicorn
   ↓
Backend validation
   ↓
Telegram Bot API
   ↓
Auto service owner
```

## 🔐 Security

Sensitive data such as the Telegram bot token and chat ID are stored in environment variables and are not included in the repository.

The backend performs its own validation instead of relying only on client-side JavaScript.

CORS is configured to allow requests from the production frontend and local development environment.

## 🚀 Local Development

Install Python dependencies:

```bash
pip install -r requirements.txt
```

Create a `.env` file:

```env
TELEGRAM_BOT_TOKEN=your_bot_token
TELEGRAM_CHAT_ID=your_chat_id
FRONTEND_ORIGIN=https://your-frontend-domain.com
```

Run the backend:

```bash
python server.py
```

Run the frontend using Live Server or another local development server.

## 📡 API

### Health Check

```http
GET /api/health
```

Example response:

```json
{
    "service": "DRIVEFIX API",
    "status": "ok"
}
```

### Create Booking

```http
POST /api/booking
```

Example request:

```json
{
    "name": "Roman",
    "phone": "+380991234567",
    "car": "Ford Focus",
    "service": "Diagnostics"
}
```

## 📌 Status

The original frontend deployment targets GitHub Pages and the Flask API targets Render. Current runtime health and real Telegram delivery have not been revalidated in this documentation-only update.

## 👨‍💻 Author

Created as a full-stack web development portfolio project.
