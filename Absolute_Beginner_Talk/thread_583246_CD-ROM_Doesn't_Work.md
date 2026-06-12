---
title: "CD-ROM Doesn't Work"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by snwbrder0721 on 2007-10-20
I just did a clean install of ubuntu on my dell (P3 733mhz, 386 ram, nvidia geforce 5500). Everything works great except my cdrom doesn't seem to show up in ubuntu. It's light is on, and it appears to "read" discs, but ubuntu doesn't seem to see it. The cd-rom is the stadard cd writer that came with the dell, I could get the specific model if needed. Any help on this is much appreciated, I'm new to linux so detailed instructions help, Thanks!

---

### Post by Pumalite on 2007-10-20
Check in /dev and see if you have a cdrom device. I doubt it. Go to BIOS and see how CD-DVD is setup. Best is 2nd Master set to 'Auto'.

---

### Post by snwbrder0721 on 2007-10-20
You're right, no cd-rom in /dev. I'll go edit the CD settings in the bios, will that solve it or do I need to do something in /dev?
Thanks!

---

### Post by snwbrder0721 on 2007-10-20
Ok, so I checked my bios, but it doesn't look like it sees a cd-rom either. I went to IDE devices and put the "atapi cd-rom" to second master on auto, but the device type reads "not installed". Maybe this is more of a hardware problem.

---

### Post by ddrichardson on 2007-10-20
Is this a desktop or a laptop?

---

### Post by snwbrder0721 on 2007-10-20
desktop, see my first post for the specs.
thanks!

---

### Post by ddrichardson on 2007-10-20
Dell uses lots of clever quick release type catches inside their desktops which sometimes work loose (they did on my Optiplex GX240).

Check the connections in the case and clean them - if you can check the drive in another machine all the better. If BIOS doesn't recognise it then there is no way any OS will.

---

