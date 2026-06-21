# ◊ FallMortgagePaper

**Sovereign MCOB-shaped document generator for UK FCA-regulated mortgage brokers.** Single HTML file. Client data never leaves the device. Prime 877.

Part of the **mortgage-firm bundle**: [fallmortgage](https://github.com/sjgant80-hub/fallmortgage) (859) · [fallmortgageonboard](https://github.com/sjgant80-hub/fallmortgageonboard) (863) · **fallmortgagepaper** (877) · [fallmortgagepractice](https://github.com/sjgant80-hub/fallmortgagepractice) (881).

Live: <https://sjgant80-hub.github.io/fallmortgagepaper/>

---

## For the end user · the 30-second pitch

You're a mortgage broker writing suitability reports, ESIS documents, IDD disclosures, and fee agreements. You're either paying for compliance software you don't own, or copy-pasting from Word templates you built three years ago. FallMortgagePaper is one HTML file that runs in your browser and generates all 12 MCOB-shaped documents — pre-populated from your client and case data, with locked regulatory clauses you can't accidentally edit.

### 12 templates

| Template | MCOB ref | Purpose |
|---|---|---|
| IDD | MCOB 4.4A/4.5/4.6 | Pre-sale firm disclosure |
| Fee Agreement | MCOB 4.4A.4R/12.5 | Broker fee, trigger, refund |
| ESIS | MCOB 5A / MCD | Pre-contract illustration |
| Suitability Report | MCOB 4.7A | Reasoned personal recommendation |
| DIP Letter | MCOB 11.6 | Decision-in-principle confirmation |
| Completion Letter | Post-completion | Confirms completion, key dates |
| Product Transfer | MCOB 4.7A.21R | Switch recommendation with existing lender |
| Redemption Request | CML handbook | Request redemption statement for remortgage |
| Complaint Ack | DISP 1.6.1R | Complaint acknowledgement |
| Final Response | DISP 1.6.2R | Complaint final response + FOS rights |
| Privacy Notice | UK GDPR Art 13/14 | Client data processing disclosure |
| Referral Letter | MCOB 2.6A | Introducer referral acknowledgement |

### How it works

1. Open the URL · demo data (James Patterson, Nationwide 2-yr fix) loads on first visit
2. **Firm** tab — set your firm name, FCA ref, address, complaints email, network statement
3. **+ Adviser** — add yourself with CeMAP, FCA ref, scope statement
4. **Cases** tab — add or sync a case from fallmortgage (client, property, loan, product, affordability)
5. **Generate** tab — pick a template, select client + case, edit sections, preview the paper document
6. **Save Draft** or **Issue** — saved to document library with SHA-256 hash
7. **Print / PDF** — opens in a new window formatted for print

### Locked vs editable sections

Regulatory clauses (MCOB, DISP, MCD, UK GDPR) are locked — marked with ◆ in the preview. You can't edit them. Everything else is editable. The suitability report rationale, alternatives, and client-specific sections are yours to write.

### Extra context

The Generate view has an "Extra Context" textarea where you enter key=value pairs for `{{ctx.*}}` placeholders — things like `dipRef`, `firstPaymentDate`, `revertRate`, `stressedMonthly`. These let you fill template-specific fields without modifying the template text.

### Audit chain (P3)

Every document save/issue appends a SHA-256 chained audit entry. Verify chain integrity from the Audit tab. Export separately.

### Cross-tool mesh

BroadcastChannel `fall-mortgage` + `fall-client` + `fall-signal`. Syncs clients, advisers, firm, and cases from sibling tools. ESIS issuance broadcasts `esis.issued` to fallmortgage.

---

## For the developer · architecture

- **Single HTML** · ~116KB · zero runtime dependencies
- **IndexedDB** (`fallmortgagepaper-v1`) · stores: firms, advisers, clients, cases, documents, templates, audit, state
- **BroadcastChannel** · `fall-mortgage` + `fall-client` + `fall-signal`
- **Template engine** · `{{path.to.value}}` placeholder resolution + `[SIGNATURE_BLOCK]` token
- **T0** · 12 hard-coded MCOB/DISP rules · zero network
- **T3** · BYOK Anthropic/OpenAI · falls back if T0 misses

### 14-pt sovereign gate

✓ Single HTML · ✓ <400KB · ✓ Sovereign · ✓ IDB primary · ✓ KONOMI shim · ✓ fall-signal mesh · ✓ PWA manifest · ✓ Mobile responsive · ✓ T0 offline · ✓ Two-audience README · ✓ MIT · ✓ .nojekyll · ✓ Demo data · ✓ Audit chain

---

## Licence

MIT · Simon Gant · part of the [sjgant80-hub](https://github.com/sjgant80-hub) sovereign estate · prime 877 · ◊·κ=1.
