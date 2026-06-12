---
title: "Ubuntu with VP6 and MegaRAID i4 card - errors up the wazoo"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by AndyInNYC on 2006-10-11
Yes, Wazoo is a technical term.

I have a Abit VP6 (dual PIII board with 2 procs) motherboard and an LSILogic i4 MegaRAID controller card (2 cards actually, tested seperately).  Same failure on the RAID array in any case.

When I install Ubuntu 6.06 (6.1 seems to completely fail to install), I get all sorts of issues.  It seems that Ubuntu somehow sees 'through' the MegaRAID card and reports not just the 1TB (5 x 250GB drives in RAID 5) array, but multiple instances of each 250 GB drive.

In addition, after installation I get write errors on a new 100 GB drive on the standard IDE channel which I'm using as my boot drive.  This causes a failure to allow logins.  The drive passes all diagnostics.

I have turned off all the 'bells and whistles' in the BIOS - the onboard Highpoint RAID, etc.

Am I alone in these issues - either with the i4 or with a VP6 - or am I failing to do something in my standard install that others have already identified?

---

