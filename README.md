# Parama – AI career companion for college students (Android, Kotlin + Jetpack Compose)

## Run it
1. Open this folder in Android Studio (Koala or newer, JDK 17). Let Gradle sync (it generates the wrapper jar).
2. Run on an emulator/device (API 26+). No paid APIs or keys are needed for the demo.

## 2-minute demo path
1. Launch → tap **Try with a sample student (demo)** (or fill the form; only name is required).
2. **Home**: greeting, goal, next recommended step, saved opportunities.
3. **Explore**: search/filter the clearly labeled SAMPLE listings → **Save** two. Open the **Roadmap** tab for skill gaps and a plan (AI-generated, labeled).
4. **Assistant**: tap a suggestion chip, or tap the mic → rationale dialog → permission → speak → edit transcript → send. Turn on read-aloud; use Stop.
5. **Profile → Resume builder**: pick a role → Generate → edit sections (placeholders appear in [brackets] for anything missing) → Share.
6. **Profile → CGPA calculator**: choose scale, add courses, edit/remove, see formula.
7. **Applications**: change status, set deadline, **Review & open** (confirmation dialog first).
8. **Profile → Upgrade**: paywall with price, renewal terms, manage link. Demo mode makes no charge.

## Architecture
- `domain/` pure Kotlin: models, GPA formula, resume generator, roadmap logic.
- `data/` local storage, sample data, `AssistantEngine` (demo rule-based engine, swap for an LLM), `BillingGateway` (Demo / RevenueCat), `SpeechController` (SpeechRecognizer + TextToSpeech).
- `ui/` Compose screens + `AppViewModel`.

## Secrets / RevenueCat
Add to `local.properties` (git-ignored): `REVENUECAT_API_KEY=goog_xxx`. With a key, `RevenueCatBilling` is used (entitlement id `plus`, first package of the current offering). Without it, `DemoBilling` is used.

## Honest scope notes
- Not yet included: resume file upload, scheduled reminders, a dedicated mock-interview session screen (interview questions are available via the assistant), and real listings/courses. All listings are fictional SAMPLE data.
- Free-tier limits in demo: 5 AI questions, 3 saved opportunities, 1 resume target.
