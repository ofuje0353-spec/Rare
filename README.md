# Favoje — 1v1 Competitive Arena

Premium, multi-page, vanilla HTML/CSS/JavaScript frontend using Firebase Authentication and Cloud Firestore. **Firebase Storage is not imported, initialized, or used.** No demo users, seeded matches, fake balances, or sample database documents are included.

## Pages
- `index.html` — Overview
- `battles.html` — Create and join open 1v1 challenges
- `rooms.html` — Create/join live rooms
- `events.html` — Published tournaments and registration interest
- `leaderboard.html` — Real Firestore user records
- `history.html` — Your battles
- `courses.html` — Published CBT courses
- `wallet.html` — Wallet and manual payment-review requests
- `notifications.html` — Personal notifications
- `profile.html` — Player profile
- `support.html` — Support tickets
- `settings.html` — Themes and sign-out
- `admin.html` — Admin review console (requires `role: "admin"` on the user's Firestore profile)
- `login.html`, `signup.html` — Authentication

## Setup
1. In Firebase Console for project `ofuje-a6c29`, enable **Authentication → Email/Password**.
2. Create a **Cloud Firestore** database.
3. In Firestore Rules, publish the included `firestore.rules` after reviewing it for your deployment.
4. Serve this folder over HTTP/HTTPS (for example, VS Code Live Server, Firebase Hosting, or any static host). ES modules generally do not work from `file://`.
5. Open `signup.html` to create your first real account.
6. For admin use, grant `role: "admin"` through a trusted Firebase Console/admin workflow. Do not allow users to set their own role.

## Important scope and production hardening
This is a functional frontend starter, not a complete production competitive platform. Authentication, Firestore-backed page reads, challenge/room creation and joining, profile editing, support tickets, payment-review requests, theme preferences and event interest are wired in. It intentionally does not fabricate question banks, opponents, wallet balances or payment confirmations.

For a production launch, add trusted Cloud Functions/server logic for:
- atomic unique username claims;
- server-authoritative battle matching, battle question delivery, clocks, scoring and results;
- rank/win/loss updates;
- payment-provider verification and wallet crediting;
- tournament bracket management and secure CBT answer validation;
- rate limiting, moderation, audit logs and anti-cheat checks.

The included rules are a starting point and must be tested against the exact workflows before launch. Client-side checks are not a security boundary. Firebase configuration values are public client identifiers; use Firebase Security Rules and App Check to protect your data. No Storage bucket is accessed by this project.
