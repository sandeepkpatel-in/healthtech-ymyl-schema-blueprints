# HealthTech YMYL Schema.org Blueprints (`@graph` JSON-LD)

Production-grade **Schema.org JSON-LD** architecture blueprints and technical QA standards for **HealthTech, MedTech, Clinical AI, and Nutraceutical** websites operating under Google’s **YMYL (Your Money, Your Life)** and **E-E-A-T** scrutiny.

Maintained by **Sandeep Kumar Patel** — Founder, [Axon Automations](https://axonautomations.in).

---

## Why This Repository Exists

Most healthcare websites fail structured data audits for three avoidable reasons:

1. **Fragmented Schema Blocks:** Dropping isolated `Article`, `Organization`, and `Person` scripts on a page without `@id` entity linking—forcing crawlers to guess relationships.
2. **Invalid Property Placement:** Placing `reviewedBy` or `lastReviewed` directly inside `Article` instead of `WebPage` / `MedicalWebPage` (triggering Schema.org validation errors).
3. **Regulatory & Parity Drift:** Marking up commercial supplement pages with clinical `MedicalCondition` / treatment claims, or injecting clinician credentials into JSON-LD that are not visibly rendered in the DOM.

These blueprints solve all three using a unified **`@graph` entity architecture**.

---

## Entity Architecture (`@graph` Relationship Model)

```text
[Organization (#organization)] ◄── publisher ── [WebSite (#website)]
         ▲                                               ▲
     publisher                                       isPartOf
         │                                               │
[MedicalWebPage / WebPage (#webpage)] ◄── mainEntityOfPage ── [Article (#article)]
   ├── author      ──► [Person (#author)]      (sameAs, knowsAbout, worksFor)
   ├── reviewedBy  ──► [Person (#reviewer)]    (hasCredential, sameAs, worksFor)
   ├── audience    ──► [MedicalAudience]       (Patient / Clinician)
   ├── about       ──► [MedicalTherapy / DietarySupplement]
   └── citation    ──► [ScholarlyArticle]      (PubMed URL / DOI)
