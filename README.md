# 240 V on a 24 V defrost board

**23 June 2025.** ATI plant, Millersburg, Oregon. Carrier packaged rooftop heat pump. Defrost control **HK32EA005** (CEPL130856-01-R). **10.5 hours** logged.

No data plate. I looked. Two-stage silk on the board (`SPPCOMPSTG2`, `DFT1` / `DFT2`). Return filters were 16x24 or 18x24, not a 5-divisible size, pulled from a hood on the side of the cabinet. That combination, on this board family, lines up with Carrier 50HCQ size 12. Inference, not a stamped SKU.

## Call

The unit had just had a contactor swapped, probably on a routine inspection. A compressor swap happened around the same job. I am fuzzy on whether that was before or after this chase. Soon after, the unit was down. The defrost board was fried. Another tech swapped the board and called it good. It went down again. I got the callback.

## What I saw

I still have both dead boards.

The older one is CEBD430856-06-RA, barcode HK32EA0052016. Aged. No burn-through.

The newer one is CEBD430856-07-RA, barcode HK32EA0055024. Cleaner face, less aged, and obviously scorched. Carbon goes through the back at the OF / L1 / fan-relay pins.

This board puts 24 V control and line-voltage fan switching on the same PCB. Electric heat is on the same board (`EHEAT`). Line from the heat strips does not belong on the 24 V side.

## Chase

I started taking voltages and found 240 V on the 24 V side of the board. That explains a lot.

I got stuck and called OEM support. They emailed the wiring diagram and left me to keep tracing. That copy lived on a work phone I no longer have. The public sheets below are the same size-12 control and power ladders from Carrier's service book — the print that closed the chase. The mix was at the auxiliary heater: 24 V control tied into 240 V line. Defrost is supposed to call the strips with 24 V. A sequencer then switches line voltage to the elements. Line from the strips should never land on the Class-2 terminals.

The prior swap was described as wire for wire. That can be true and still kill the next board. If the landing is wrong, copying the landing copies the fault.

## Fix

New contactor. New board. Wired to the print. It ran. 10.5 hours on the job.

## What I am not claiming

This is a field postmortem, not a software project. I do not have a stamped cabinet SKU. 50HCQ size 12 is a filter-and-silk fit, not a plate reading. No street address, account number, or other tech's name. The two ladder sheets are Carrier service-manual figures (50HCQ-4-12-02SM, Appendix E, Fig. I and Fig. Q). Not the lost job email, not the heater-kit book.

## Photos

Both failed boards, on the bench, 24 Aug 2026.

![Older board, front](photos/05-original-front.jpg)

CEBD430856-06-RA. HK32EA0052016. EHEAT, DFT1/DFT2, INTERVAL TIME 30/60/90.

![Older board, back](photos/06-original-back.jpg)

No burn-through.

![Newer board, front](photos/07-new-front.jpg)

CEBD430856-07-RA. HK32EA0055024. Less aged.

![Newer board, back](photos/08-new-back.jpg)

Scorch through the solder mask at the fan-relay / OF / L1 corner.

## Print

The two sheets I sat with. Size-12 control ladder and 208/230-3 power ladder.

![50HCQ*12 control wiring](photos/09-control-ladder-50hcq12.png)

Fig. I — 50HCQ*12 control. Two compressors. Defrost board left, CTB right. Source: Carrier 50HCQ-4-12-02SM p.92.

![50HCQ*12 power wiring](photos/10-power-ladder-50hcq12.png)

Fig. Q — 50HCQ*12 power, 208/230-3-60. Source: same book, p.100.
