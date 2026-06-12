---
title: "Feisty Install Frozen at 82%"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by reidamd on 2007-04-27
I'm trying to install feisty from the live CD. I did a CD check and it looks good. It is however freezing at 82% of install at the Configuring apt "scanning the mirror" phase. Does anyone have any idea what is going on at this point of the install??

---

### Post by Najand on 2007-04-27
Do you have a weak connenction to the internet or are you behind a proxy server? If so, disconnect it from the internet and then try again!

---

### Post by reidamd on 2007-04-27
Okay, I have to manually set my mtu to 1400, because it doesnt work at 1500. I went into bios and disabled my network card all together, just to rule it out, and it installed fine. Rebooted, re-enabled driver in bios opened terminal:

sudo ifconfig eth0 mtu 1400

Now, everything works fine and I can resolve DNS. I'm copying WoW CDs to my linux partition now, so I can try it out in WINE. Also when I reinstalled, my nvidia drivers installed fine through restriced drivers. It' my first day using linux,  and so far I like it alot, especially the open source part. Thank you for your help.

---

### Post by dcraigp2002 on 2007-04-27
Leave it alone. Mine froze at 82% for about ten minutes and then moved on.

---

### Post by Najand on 2007-04-27
Good you like that.... Thank you too for using Linux.

---

