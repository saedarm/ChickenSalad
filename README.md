# Chicken Salad Chick Lunch Order Form — Google Apps Script

Programmatically builds a Google Form for collecting Chicken Salad Chick box lunch orders from a group. Built for a school catering order at 11pm. It shows.

## What it does

Runs once from Google Apps Script and creates a fully configured Google Form in your Drive with:

- Email collection
- 6 branching paths (3 entree types × 2 side counts)
- 45 regular sandwich options (15 flavors × 3 breads)
- 14 scoop options (flavor only — comes with crackers)
- 51 signature / BLT options (15 BLT flavors × 3 breads + 6 Turkey Club variants)
- 11 specific side options (4 salads/fruit + 7 individual chip varieties)
- Exactly-2-sides validation enforced on two-sides paths
- All 6 paths route explicitly to End — no accidental section bleed

## Files

| File | Description |
|------|-------------|
| `createLunchForm_v1.gs` | Initial version — 2 paths (sandwich only, generic sides) |
| `createLunchForm_v3_final.gs` | Final version — 6 paths, all entree types, full sides list, correct routing |

## How to use

1. Open any Google Sheet in your Drive
2. Go to **Extensions → Apps Script**
3. Paste the contents of `createLunchForm_v3_final.gs` into the editor
4. In the function dropdown at the top, select **`createLunchForm`**
5. Click **Run** (not Deploy — do not deploy this as a web app)
6. Check the Apps Script console for the Edit URL and Published URL

The form will appear in your Google Drive root. Share the Published URL with your group.

## Common mistake

Do not click **Deploy → New deployment** and run it as a web app. That path expects a `doGet` function and will throw `Script function not found: doGet`. This script is not a web app — it is a one-time runner. Just hit **Run**.

## Customization

All data lives in arrays at the top of the script. To update dates, prices, flavor names, or side options, edit the relevant array and re-run. Delete the old form from Drive first to avoid duplicates.

To change the form description and deadline, update the `form.setDescription()` call.

## Menu context

Built against the Chicken Salad Chick catering menu (Centerville, OH location). Menu options extracted from the live ordering page HTML via browser DevTools. If CSC has updated their menu since this was written, update the arrays accordingly.

Notably: Dixie Chick is not available as a scoop. This is reflected correctly in `scoopOptions`.

## Related

Full writeup of how this came together — including the Microsoft Forms detour, the Form Migrator betrayal, the combinatorics crisis, and the `CONTINUE` routing bug — published on Medium under the S.A. Routh byline.
