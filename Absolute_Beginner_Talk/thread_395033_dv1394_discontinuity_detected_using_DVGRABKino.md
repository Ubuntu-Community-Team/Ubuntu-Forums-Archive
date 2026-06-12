---
title: "dv1394: discontinuity detected using DVGRAB/Kino"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by adam s on 2007-03-27
Hi,


I am now able to grab data from my DV Camcorder using fire wire and DvGrab.

The picture quality is pathetic and when I look at the dmesg I get the following :


[17262609.948000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[COLOR="Red"][17262664.620000] dv1394: discontinuity detected, dropping all frames[/COLOR]
[17262877.184000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[17262877.184000] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[08004601035625e2]
[17266036.752000] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[08004601035625e2]
[17266036.752000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[17267300.496000] dv1394: discontinuity detected, dropping all frames
[17268269.536000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[17268269.536000] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[08004601035625e2]
[17268285.812000] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[08004601035625e2]
[17268285.812000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[17269136.492000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[17269136.492000] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[08004601035625e2]
[17269139.008000] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[08004601035625e2]
[17269139.008000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023

I have coloured in the relevant part.....

Any ideas where to go from here - I am running kernel 2.6.15-28-386

Thanks for your help,

Adam.

---

### Post by adam s on 2007-03-28
bumping up....has anyone had any experience of this and know if one can fix it?

---

