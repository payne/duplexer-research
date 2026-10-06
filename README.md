# UHF Duplexer Research for an M17 Repeater

*Researched 2026-10-06*

## Background

Following Rob Robinette's guide, [Building an M17 Repeater](https://robrobinette.com/Ham_VHF-UHF_Digital_Modes.htm#Building_an_M17_Repeater). The guide uses two UHF radios, an STM32 DVM controller and a duplexer.

- **Controller:** [STM32_DVM_Combo](https://www.repeater-builder.com/products/stm32-dvm.html) (arrived)
- **Goal:** a low-power repeater for learning and experimenting
- **Repeater pair:** output (repeater transmit) **441.2750 MHz**, input (repeater receive) **446.2750 MHz**, a 5 MHz gap

### Original question (email to Rob, Matt, Jeff, Jim)

> My `STM32_DVM_Combo` has arrived and I'm now looking for a duplexer. My current goal is a low power repeater for learning and experimenting. My repeater pair has an output frequency of 441.2750 and input of 446.2750 MHz. I'm just starting to read about duplexers. Would you please tell me if any of these will work?
>
> 1: https://www.amazon.com/gp/product/B07FGFX6Q4/
> 2: https://www.amazon.com/gp/product/B08SVWQBDD
> 3: https://www.amazon.com/gp/product/B0GYYH2NNR
> 4: https://www.amazon.com/gp/product/B0G3X7JS6L
>
> And which would be easiest for a new person like me to get working?
>
> Thanks! -- Matt N3PAY

## Short answer

#1 and #2 will work if they're retuned to 441.275/446.275, and #4 might. Skip #3. The easiest one for a beginner is **#1 or #2 ordered already tuned to your pair**. None of the four comes tuned to these frequencies, and doing that tuning yourself is the hard part.

## The four listings

All four are the same kind of small, cheap "mobile" duplexer: six little filter cavities in one box, N-female connectors. Three of them ship tuned for GMRS (462/467 MHz), about 21 MHz above this pair, so every one needs retuning.

| # | What it is | Price | Will it work for 441.275 / 446.275? |
|---|---|---|---|
| 1 | [Fumei 50W](https://www.amazon.com/gp/product/B07FGFX6Q4/), sold by DotDotTech, ships from Amazon | $119 | **Yes, once retuned.** It tunes across 400–470 MHz. 120 reviews averaging 3.8 stars, and several people report it working well on low-power repeaters. |
| 2 | [Fumei 30W](https://www.amazon.com/gp/product/B08SVWQBDD), same seller | $90 | **Yes, once retuned.** Reviewers say it's the same box as #1 with a lower power rating. 30W is plenty for low power. 38 reviews, 3.9 stars. |
| 3 | [Fesjoy "450 type" 25W](https://www.amazon.com/gp/product/B0GYYH2NNR) | $83 | **Skip it.** It's fixed at 456.175/466.175 and specified for an 8–10 MHz gap between the two frequencies. This pair's gap is 5 MHz. No reviews; delivery Oct 19–29. |
| 4 | [Generic 50W](https://www.amazon.com/gp/product/B0G3X7JS6L), sold by AliceWonderBag | $85 | **Maybe.** The listing says it tunes from 380–520 MHz with a minimum 3.5 MHz gap. It looks like a copy of #1, but it has no reviews and is sold by a third party. 1-year warranty. |

### Listed specs

| | #1 Fumei 50W | #2 Fumei 30W | #3 Fesjoy | #4 Generic |
|---|---|---|---|---|
| Max power | 50W | 30W | 25W | 50W |
| Range | 400–470 MHz | 400–470 MHz | fixed 456.175 / 466.175 | 380–520 MHz |
| Minimum gap | not stated | not stated | 8–10 MHz | 3.5 MHz |
| Insertion loss | <1 dB (claimed) | <1 dB (claimed) | ≤1.0 dB | <1 dB (claimed) |
| Isolation | >80 dB | >80 dB | >75 dB | >80 dB |
| Factory tuning | 462 / 467 MHz | 462 / 467 MHz | 456.175 / 466.175 | 462 / 467 MHz |
| Custom tuning offered | yes, contact seller | yes, contact seller | no | yes, contact seller |

## What reviewers said

- **Tuning equipment:** reviewers keep saying retuning needs a good network analyzer or a spectrum analyzer with a tracking generator. Several said a NanoVNA can't measure deep enough to set the notches properly. One said it took about 10 minutes with a proper analyzer. Another said the tuning screws are touchy and the notch shifts while tightening the locknuts.
- **5 MHz gap:** one reviewer tuned #2 to 80 dB isolation at a 5 MHz gap, but it cost a couple of dB of extra loss on the low side. They thought it was really designed for a 10 MHz gap.
- **Insertion loss:** good units measured about 1.1–1.5 dB per side. One reviewer measured 15.1W in and 13.9W out. A couple of bad units showed 10 dB or more.
- **Factory tuning varies:** some units arrived spot on, others about 2 MHz off, and one had a weak notch on one side.
- **Desense:** the 1-star reviews are mostly about desense (the repeater's transmitter deafening its own receiver), worse at higher power and with sensitive repeaters.
- **Durability:** one reviewer running a full 50W had the Teflon insulators burn through over a winter, and replacement parts weren't available.
- **Size (#1):** about 1.5 × 7.5 × 8.75 in, too big to fit inside some commercial repeater cases.

## Recommendation

Buy #1 (or #2 to save $30) and **message DotDotTech before ordering**. Ask them to factory-tune it with:

- **Low side: 441.275 MHz**, connected to the repeater's transmitter
- **High side: 446.275 MHz**, connected to the repeater's receiver

Then it's ready to connect out of the box.

## Things to know

- **Expect some loss:** about 1–1.5 dB through each side on a good unit. Check yours when it arrives.
- **Start low on power:** begin at a few watts and test for desense by keying the repeater while listening for weak signals.
- **Stay well under the rated power** to avoid the insulator failures reviewers described.
- **Connectors:** these have N-female connectors, so you'll probably need N-to-PL-259 adapters or jumpers for the radios.
- **Low-cost fallback:** for a low-power learning setup, two separate antennas, one mounted several feet directly above the other, can work instead of a duplexer.
- **Ask around:** Rob and the others on the thread may know local hams with a service monitor who could check or tune it.


