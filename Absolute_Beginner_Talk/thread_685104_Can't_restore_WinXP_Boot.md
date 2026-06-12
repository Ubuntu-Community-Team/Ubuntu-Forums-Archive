---
title: "Can't restore WinXP Boot"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Aphaits on 2008-02-01
okey dokey, seems like I'm a bit in doodoo now

prior events in chronological order:
- curious about Ubuntu
- installed second IDE HDD for trying Ubuntu (first is SATA)
- Ubuntu installs without a hitch
- restarts PC, Ubuntu goes haywire (hardware-compatibility wise)
- loaded up WinXP from HDD no.1
- (foolishly) reformatted IDE HDD to remove Ubuntu
- weird Grub error shows up, won't load WinXP
- removed 2nd IDE HDD
- started PC, and error shows up

well currently, can't boot WinXP
and this error kept showing up:
---
GRUB Loading stage1.5

GRUB loading, please wait...
Error 21
---

I guess I'll have to try Ubuntu on a different machine without dual-booting,
but in the meantime, I can't load my main WinXP work-PC.
(and clients are waiting)

thanks for any tips
-Aphaits-in-trouble-

---

### Post by taurus on 2008-02-01
Boot your machine into recovery mode with XP disc and remove GRUB from MBR with fixmbr.

Or [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Amstell on 2008-02-01
install super grub....that always worked for me.  But one time i got that error 21 and had to reformat everything.  Good luck though

---

### Post by Aphaits on 2008-02-01
is there anyway to fix MBR without the WinXP cd?
I'm rummaging my room and I can't seem to find it.
(Where the heck is my WinXP CD???)

---

### Post by Aphaits on 2008-02-01
> **Amstell said:**
> install super grub....that always worked for me.  But one time i got that error 21 and had to reformat everything.  Good luck though

that is another option, but I prefer restoring the booting part to my original Windows (or is it DOS?)
thanks for the tip

---

