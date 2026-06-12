---
title: "dual-drive boot problem"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by tefflox on 2006-07-07
Today I got a new sata drive and installed it on 0, and my old sata drive with windows xp (and the same version of ubuntu on an extended partition) --installed the old sata drive on 1.  What I want to do, without changing the present hardware configuration, if possible, is make the sata 0 drive allow a roll-over boot from the second drive.

I'm able to mount the second drive's ubuntu installation just fine in the first sata drive, but I can't get the grub config to get to the second drive.  My alternate OS listing in grub looks like this:

title Windows...
root (hd1,0)
map(hd0,hd1)
map(hd1,hd0)
chainloader +1

What can I do?

---

### Post by sumitsen on 2006-07-07
Hi tefflox,

Can you check if the ubuntu drive (hd1) is the first drive to load in the bios. I think right now your windowsxp drive is set as the first one to load in bios. Get the fixed and the dual boot shall work.

Cheers, SUmit

---

### Post by tefflox on 2006-07-07
actually hd0,0 loads first. thx

---

