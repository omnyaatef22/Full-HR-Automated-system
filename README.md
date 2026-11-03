# Horizon Byte People Portal

An interactive HR portal built on five n8n workflows.

**For candidates**, the home page offers three stages:

1. **Ask**: an HR Policy Assistant (RAG). Answers come only from the policy documents and name their source.
2. **Prepare**: a Job Application Coach. A career-coach agent runs three specialist agents (CV Matcher, Cover Letter Writer, Interview Coach). The summary shows on screen and the full report is emailed.
3. **Apply**: an application form with the same checks as the intake workflow (full name, email, a real PDF under 5 MB, duplicate detection).

**For the HR team**:

- **Recruiter agent**: hourly batch screening. CVs are read (OCR for scans), profiled, scored against the role, checked by a guardrail, then routed to interview, HR review or a polite decline.
- **System health**: error classification, alert throttling, a heartbeat for a stalled queue, and a daily digest.
- **Workflows**: each n8n workflow drawn node by node, with sanitized JSON downloads.

## Demo mode and live mode

With no n8n address configured, the site runs a demo: sample candidates and policies (all fictional), and in-browser stand-ins for the AI steps.

To connect your n8n instance, open `index.html` and set:

```js
const CONFIG = {
  n8nBase: "https://your-domain.ngrok-free.app",
  ...
};
```

Then in n8n:

- Activate the intake, coach and policy-upload workflows (their forms open in a new tab).
- In the **Employee Question** chat trigger, turn on **Make Chat Publicly Available**, choose **Embedded Chat**, and add this site's address (for example `https://<username>.github.io`) to **Allowed Origins (CORS)**.

## Files

- `index.html`: the whole site, with no build step.
- `n8n-*.json`: the five n8n workflows with credentials, sheet IDs, folder IDs and email addresses removed. Import them into n8n and reconnect your own credentials.

Built with n8n by Omneya.
