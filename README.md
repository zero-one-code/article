# Herpes Zoster Vaccine DOM Page

This version keeps only the main section structure in `index.html` and builds the detailed visual elements with DOM methods in `script.js`.

Updates included:
- The uncertainty/mean indicators in dot plots use the original `mean1.png`, `mean2.png`, `mean3.png`, and `mean4.png` assets.
- The mean/range image is placed behind the generated dots so the original dot-and-gradient look is preserved.
- The arrow icons use `arrow1.png` and `arrow2.png` from the `assets` folder.
- CSS is separated in `style.css`, following the external stylesheet structure used in the lecture material.

Open `index.html` in a browser to view the page.

- Added final thank-you message at the end of the closing section.


Update: Final survey-return message font size was set to 46px and the page bottom spacing was reduced.

Motion/interactions added in this version:
- Scroll-triggered reveal for titles, text cards, illustrations, charts, and comparison blocks.
- Dot plots now animate from neutral grey dots to highlighted cases when the plot enters the viewport.
- Confidence interval bars expand on reveal, and mean markers appear after the range expansion.
- Mean values in simple charts count up on viewport entry.
- Comparison sections use staged reveal for labels, group plots, VS badge, arrow, and legend.
- A fixed section progress rail was added for long-form navigation.
- `prefers-reduced-motion` is respected for accessibility.

Open `index.html` in a browser to view the animated version.

Scroll interaction smoothing pass:
- Pinned visual layers now use a viewport-aware scale so 1920x1080 scenes do not crop on shorter screens.
- Fixed-layer handoffs were retimed to avoid overlaps between disease, risk, vaccine, effectiveness, and reliability scenes.
- The effectiveness comparison now fades into the summary card as an overlay, instead of leaving a blank or low-position card.
- Fast scrolls catch up more quickly, while small scroll deltas remain eased for smooth reading.

Latest interaction polish:
- The herpes zoster diagram handoff now keeps the pinned layer at the same width-based scale as the static canvas layer, preventing a sudden size shrink while scrolling.
- The risk-group scene now exits with a slow opacity dissolve and only a small lift, rather than a large upward jump.
- The vaccination intro scene now fades in gradually after the risk-group page fades out, creating a softer page-to-page transition.

Revision pass 2026-07-07:
- Added a slower fade-in for the placebo effectiveness chart and its canvas dots.
- Changed the main effectiveness mean label to a scroll-tied count-up from 0 to the target value, so the placebo mean visibly counts from 0 to 33.
- Retimed the vaccinated speech card so the vaccinated background remains unchanged until the card has fully left the screen.
- Retimed the effectiveness summary card so it scrolls completely off the top before the comparison background fades away.

Timing patch for effectiveness count-up cards:
- The placebo message card now waits until the scroll-tied Mean value has finished counting from 0 to 33 before entering.
- The vaccinated message card now waits until the Mean value has finished counting from 0 to 16 before entering.
- The single dot-chart background is held stable while each message card moves upward, and only collapses/changes phase after the corresponding card has moved off-screen.

Timing update:
- The placebo mean now counts from 0 to 33 over a short continuous scroll interval before the placebo speech card appears.
- The vaccinated mean now counts from 0 to 16 before the “Approximately…” speech card appears.
- The vaccinated chart remains unchanged until the “Approximately…” card has fully passed upward.
- The comparison screen (“The Effectiveness of Vaccination”) fades in only after the vaccinated chart/card sequence exits; its summary card passes over the comparison background, and the background fades only after that card has disappeared.

Latest timing/layout pass:
- The effectiveness comparison composition was moved lower in the fixed design frame so it sits closer to the screen centre.
- The effectiveness summary card now pauses around the vertical centre before scrolling upward and fading only after it exits.
- The reliability title was moved lower and remains visible while its speech card passes over it; only after the card leaves does the fixed layer fade, revealing the next uncertainty screen underneath.
- Placebo and vaccinated mean values now count up over a shorter, continuous progress interval so one normal scroll gesture can carry the number from 0 to the target value.

Latest sequence polish:
- The effectiveness comparison now waits until all comparison elements are visible before the summary card rises from the bottom.
- The comparison background is held until the summary card has left, then fades only at the very end of the pinned scene.
- The reliability card now hands off into a fixed uncertainty-types sequence: the uncertainty-types image fades in at screen center, the “The data in this study...” card scrolls over it, and the target-population/sample image fades in only after that card has gone.

Latest target-sample uncertainty sequence polish:
- The target population / Sample 1 diagram is now part of the pinned scrollytelling sequence.
- After that first sample diagram is fully visible, the "This study did not include..." card travels upward over it until it leaves the viewport.
- The multiple-samples diagram then cross-fades in over the first sample diagram.
- After the multiple-samples diagram is visible, the "Therefore, the result could vary..." card travels upward over it before the confidence interval section appears.

Advanced target/sample transition:
- Replaced the full-image crossfade between Sample 1 and Multiple samples with a layered transition.
- The common target-population image now remains visually stable while a small white wipe clears only the old right-side Sample 1 area.
- Only the changed right-side elements from the multiple-samples diagram are revealed, preventing the double-image/ghosting that happened when two full diagrams overlapped.

PDF-order uncertainty sequence fix:
- Reworked the uncertainty fixed scene to explicitly follow the requested visual order: Target Population / Sample 1, then Multiple Samples, then Samples → Confidence Interval.
- Removed the clipped/right-side overlay transition for the multiple-samples visual because it was not visibly reflecting the requested full-scene order.
- Added clear progress windows so Sample 1 remains visible while its speech card passes, Multiple Samples appears only after that card has left, and the Confidence Interval visual appears only after the Therefore card has passed.
- Confirmed the scene uses the supplied assets in `assets/target_population_sample_transparent_highres.png`, `assets/target_population_multiple_samples_transparent_highres.png`, and `assets/samples_confidence_interval_transparent_highres.png`.

Latest uncertainty sequence timing update:
- Preserved the existing flow: uncertainty types → target population/sample 1 → multiple samples → confidence interval → likely-range transition.
- Added the requested speech-bubble timing: each card passes from bottom to top only after its background visual has fully appeared.
- Added the final “Now, let’s look...” card over a blank white background after the confidence-interval card has passed.
- Standardized speech-bubble card width and text sizing across generated cards and pinned scrollytelling cards.

Likely-range transition smoothing pass:
- Removed the duplicate static Placebo likely-range chart/card that was rendering underneath the pinned version and causing an uneven crossfade/drift.
- The Placebo likely-range chart is now handled by a single fixed pinned scene, with a higher z-index so it fully covers the preceding uncertainty sequence.
- Dot expansion is scroll-tied using the same cluster-to-grid morphing pattern as the earlier placebo dot scene.
- The 30~36 / Mean 33 count-up is also scroll-tied, and the explanatory card starts only after the chart, dots, and count-up have settled.
