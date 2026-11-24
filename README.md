# JBL Learning Assistant

Build a clickable React prototype (single-page app, mock data only, no real backend) 

demonstrating two AI features for JBL, a nursing/EMS-focused digital textbook and 

course-materials platform owned by Ascend Learning. This is for an internal 

stakeholder presentation — prioritize visual polish, realistic sample data, and 

smooth micro-interactions over real functionality. All AI responses should be 

pre-scripted/mocked (no live API calls needed) but should feel like they're 

"generating" via short simulated loading states.

=== GLOBAL REQUIREMENTS ===

- Match the existing JBL platform's design system, layout patterns, and UX 

  conventions where known (e.g., shared Magento cart styling, My Account 

  widget, UA login widget look-and-feel); if no reference screenshots/design 

  system are provided, fall back to the clean clinical-education style 

  described below and flag this assumption clearly at the top of the output.

- Use a role switcher in the top nav: Student | Instructor | Admin | Sales/Ops 

  (clicking switches the entire view context)

- Use a clean, modern clinical-education visual style: white background, one 

  primary accent color (deep teal or navy — pick one and use consistently), 

  clear typography hierarchy, generous whitespace. Avoid generic "AI purple 

  gradient" clichés.

- Every AI-generated element must visually distinguish itself from static content 

  (e.g., a subtle icon, border treatment, or "AI" tag) so the demo audience can 

  always tell what's AI vs. what's platform UI.

- Include a persistent "Reset Demo" button that restores all mock data to its 

  initial state.

- Build for a laptop/browser presentation (1440px width baseline), not mobile.

=== FLOW 1: StudyBot (Student + Instructor + Admin views) ===

Sample content: create ONE realistic mock nursing textbook chapter (~400-600 

words) on a clinical topic (e.g., "Chapter 7: Managing Sepsis in Adult Patients") 

with 3-4 subsections. Use this same chapter across all StudyBot interactions so 

citations are consistent.

STUDENT VIEW:

- A book reader panel (left, ~65% width) showing the mock chapter text, scrollable

- A "StudyBot" side panel (right, ~35% width) with:

  - A chat input ("Ask a question about this chapter...")

  - When the student types/sends a question, show a realistic typing/thinking 

    indicator (~1.5s), then reveal an answer

  - The answer must include: the response text, a highlighted quoted excerpt 

    from the chapter it's grounded in (click to jump/scroll to that spot in the 

    reader), and a small confidence indicator (e.g., a colored dot or percentage)

  - Pre-script at least 3 sample Q&A pairs tied to different parts of the chapter, 

    plus a graceful "I can only answer based on this chapter's content" response 

    if the user asks something clearly out of scope (include one such example)

  - Buttons: "Generate Quiz" (produces 5 multiple-choice questions, each showing 

    a small "based on paragraph X" tag), "Generate Flashcards" (produces 5 

    front/back flip cards), "Summarize Chapter" (produces a 4-5 bullet summary)

  - Each generated artifact should have its own loading animation and appear in 

    an expandable card within the panel, dismissible/collapsible

INSTRUCTOR VIEW (toggle via role switcher):

- Shows the same chapter plus a "Review AI-Generated Quiz" panel

- Displays the 5 quiz questions from the student flow, each with Edit/Approve/

  Reject controls and a status badge (Pending Review / Approved / Edited)

- Include one question pre-flagged as "Edited by instructor" with a visible 

  diff or "before/after" toggle to show human correction in action

- An "Assign to class" button that becomes enabled only once all questions are 

  Approved or Edited (never Pending)

ADMIN VIEW (toggle via role switcher):

- A simple table of 4-5 mock titles with columns: Title, AI-Enabled (toggle 

  switch), Exposure Policy Status (Signed Off / Pending Legal Review), Usage 

  (mock number like "1,204 questions this month")

- Clicking a title's "Exposure Policy Status" opens a modal showing a mock 

  policy: "Allow: chapter summaries, flashcards (max 50 words/card); Disallow: 

  full text export, image OCR" with a "Signed off by [Name], [Date]" line

- The AI-Enabled toggle should be disabled/grayed out for any title where the 

  exposure policy isn't signed off, with a tooltip explaining why — this is the 

  key trust beat, make it visually obvious

=== FLOW 2: CRM ↔ Catalogue Match Assistant (Sales/Ops view) ===

- A "Run Match Job" button that, when clicked, shows a brief processing 

  animation (~2s) then populates a results table

- Mock CRM data (5-7 rows): institution name, CRM account ID, proposed JBL 

  account ID, confidence score (as a percentage + color-coded bar: green 

  >85%, yellow 60-85%, red <60%)

- Include: 4 clean high-confidence matches, 1 medium-confidence match, 1 

  deliberate conflict (one CRM account proposing matches to two different JBL 

  accounts — this should visually stand out, e.g. red border/warning icon)

- Clicking any row expands an "Evidence" panel showing: matched email domain, 

  billing address similarity, recent order ID overlap — presented as a simple 

  checklist with checkmarks/x-marks, not just a paragraph

- Each row has Accept / Reject / Edit Rule actions. Accepting should visually 

  move the row to a "Confirmed" section with a timestamp and "by [Sales User]" 

  attribution (mock an audit trail)

- The conflict row should require the user to manually pick which match is 

  correct (a modal with the two options side by side) before it can be resolved

- Include a small "Audit Log" tab/section showing a running list of the last 

  5 actions taken (e.g., "Accepted: State University match — 9:42am")

- A "Suggest Rule" moment: after accepting 2-3 matches with the same pattern 

  (e.g., matching email domain), show a small AI suggestion banner: "Noticed a 

  pattern — auto-suggest matches with matching email domain going forward?" 

  with Accept/Dismiss buttons (purely cosmetic for the demo, no real logic needed)

=== MICRO-INTERACTIONS TO INCLUDE THROUGHOUT ===

- All "AI thinking" states use a subtle animated indicator, never a blank pause

- Hover states on all interactive elements (buttons, table rows, cards)

- Smooth expand/collapse transitions for cards and panels (200-300ms ease)

- Toast/snackbar confirmations for actions (e.g., "Match confirmed", "Quiz 

  assigned to class")

- The role switcher should have a brief transition when changing views, not 

  an instant jarring swap

=== WHAT NOT TO BUILD ===

- No real authentication, no real backend, no real AI API calls

- No need for the full catalog/storefronts (Burlington/PSG/CDX) — one mock 

  title is enough for Flow 1

- No payment/checkout flow

Build this as a single React app (functional components, hooks only, no 

external state library needed — component state or Context is fine). Keep all 

mock data in a clearly separated data file/object at the top so it's easy to 

edit before the actual presentation.

This project was built with [Lovable](https://lovable.dev).

**Live app**: https://jbl-ai-pilot.lovable.app

## Build with Lovable

Continue developing this project in the [Lovable editor](https://lovable.dev/projects/08d1da25-f815-49a0-b13e-1066bf7bb03c).

- **Ship faster**: describe what you want to build and Lovable handles the code.
- **Stay in sync**: every change made in Lovable is committed straight to this repository.
- **Full ownership**: this code is yours. Push to `main` on GitHub and your changes sync back into Lovable, ready for your next prompt.

## Development

Prefer working locally? You need Node.js and npm — [install with nvm](https://github.com/nvm-sh/nvm#installing-and-updating).

```sh
git clone <this-repository-url>
cd <repository-name>
npm i
npm run dev
```
