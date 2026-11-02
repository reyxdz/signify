# Signify

Where signing is simplified. Upload a PDF, place signature fields on the
pages, and email a link. The recipient opens that link and signs there.

---

## What you can do

- **Sign in** with an email and password, or with Google.
- **Save a signature** by drawing one, or by choosing a premade signature
  and initials.
- **Prepare a document.** Upload a PDF, drop signature fields on it, and
  assign each field to a recipient.
- **Send it.** Publishing emails each recipient a link to the document.
- **Finish.** Export a PDF with the signatures placed on the pages.
- **Look back.** The dashboard shows document counts, your files, files
  shared with you, your signature, and an activity list.

---

## Stack

| Layer | Choice |
|---|---|
| Web | React 19, Create React App |
| API | Express 4 |
| Database | MongoDB, via Mongoose |
| PDF | pdf-lib on the server, react-pdf in the browser |
| Email | Nodemailer, through Gmail |
| Auth | JWT, and Google sign-in |

The web app runs on port 3000 and calls the API at
`http://localhost:5000`.

---

## Getting started

Requires Node.js, npm, and MongoDB listening on
`mongodb://localhost:27017/signify`.

```bash
# API
cd server
npm install
npm run dev

# Web, in a second terminal
cd signify
npm install
npm start
```

Open <http://localhost:3000>.

Password sign-in works once both processes are up. Signing emails and
Google sign-in need env files, and those files are gitignored.

Signing emails, in `server/.env`:

```env
EMAIL_USER=your-email@gmail.com
EMAIL_PASSWORD=your-gmail-app-password
JWT_SECRET=change-me
REACT_APP_SIGNING_URL=http://localhost:3000/sign
```

Google sign-in, in `signify/.env`:

```env
REACT_APP_GOOGLE_CLIENT_ID=your-client-id.apps.googleusercontent.com
```

How to create those values:
[EMAIL_SETUP.md](./EMAIL_SETUP.md) and
[Docs/GOOGLE_OAUTH_SETUP.md](./Docs/GOOGLE_OAUTH_SETUP.md).

---

## Layout

```
signify/
├── signify/             React app
├── server/              Express API and Mongoose models
├── Docs/                Setup notes
└── API Documentation/   Endpoint reference
```

Endpoint reference:
[API Documentation/API_ENDPOINTS.md](./API%20Documentation/API_ENDPOINTS.md).
Publish, recipient signing, decline, and PDF export are implemented in
`server/index.js`.
