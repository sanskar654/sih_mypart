# /onboarding — Track A (Ethan)

IVR call flow, WhatsApp verification, Pahchan ID OCR. See Section 2.1 and 5.1 of
`docs/Kaarigar_Prototype_Master_Document.docx`.

This folder is owned by Track A — Track C only left this placeholder so the repo
structure from Section 6 exists from day one.

## What Track C already built for you

The shared backend (`/backend`) is running and exposes the endpoints you need:

| Call | When to use it |
| --- | --- |
| `POST /api/artisans` | After OCR extracts name / village / craft from the Pahchan ID. Body: `{name, phone, village, craft_type, story, verified}`. Returns the artisan with its `id`. |
| `POST /api/artisans/{id}/verify` | Once the artisan replies `YES` to the OCR read-back. Flips `verified` to true. |
| `GET /api/artisans` | List everyone (useful for checking "does this phone number already have an account?"). |

Publishing a listing is blocked with HTTP 403 until an artisan is verified, so the
Pahchan gate is enforced by the backend, not just by your call flow.

Base URL locally: `http://localhost:8000`
