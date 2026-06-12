---
title: "Wifi support for new Mac Mini?"
date: 2009-05-25
forum: Apple Hardware Users
---

### Post by chrispoole on 2009-05-25
Hi,
I'm trying to find out how compatible the new Mac Mini (with 9400M graphics chipset) is with Ubuntu (Mythbuntu in particular).

Can anyone point me to somewhere confirming that the graphics card and wireless device is supported, or let me know otherwise?

I can't find any detailed specs of the Mini either, and don't own it yet so can't check with lspci, etc.

Thanks.

---

### Post by hajk on 2009-06-02
The new Broadcom hybrid-sta driver (wl.ko) should work on your wireless.
The latest nvidia driver works, except it cannot handle the Apple LED Cinema Display or any other display using the MDP connector (for that you need to use the vesa driver). Displays using the mini-DVI connector are fine. Sound may need some trial-and-error, the "model=imac24" option for the hda_snd_intel driver seems to work.

Have fun!

---

