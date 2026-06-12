---
title: "hdparm caused PS2 mouse/keyboard probs"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by getut on 2007-01-27
Oh boy... I've successfully made mincemeat out of my first Ubuntu install after having it going nicely for weeks now.

I was following instructions on the Ubuntuguide for Edgy wiki page for tweaking (specifically the part about using hdparm to tweak DMA for CDROM section) and now my PS2 mouse and keyboard are cycling on and off every 10-20 seconds or so.

I have no idea how to recover from this. I couldn't even get anything typed in.. luckily I have a USB mouse and keyboard handy that I hooked up to type this.

Everything SEEMED to go wrong right after the command sudo hdparm -d1 /dev/hda but I've rebooted multiple times and even done the same commands with -d0 to set it back if that was what had caused the issue.

I'm lost. Please help me.

---

### Post by riven0 on 2007-01-27
Well, I'm kinda lost, too. But have you tried going into your BIOS and try disabling DMA completely? 

Sorry I can't be of better help. Never ran into this problem before, and I've done DMA tweaks.

---

### Post by getut on 2007-01-27
<Sheepish grin>

Ok...I'm going to take the moral high road on this, be a big man and admit my stupidity. I even work in the ITfield so the fact that this escaped me is all the more embarrassing.

I found the problem. I have a KVM switch and I inadvertently hit the option to go into scan mode. BUTIN MY OWN DeFENSE (heheh) this is the first time I have done that since building my new rig with new LCD monitor. I have the video input bypassing the KVM switch on one of the two inputs and THROUGH the switch on the other input. The mouse and keyboard were cycling from one PC to the other while my view on the monitor was staying on my new Ubuntu box. Last time I hit that sequence of keys I had an old tube monitor with only 1 input so the screen switched each time the mouse and keyboard did.

Ok... I'm going to bed now. Can someone DELETE this thread to save my embarrassment?  :oops: #-o :D

---

