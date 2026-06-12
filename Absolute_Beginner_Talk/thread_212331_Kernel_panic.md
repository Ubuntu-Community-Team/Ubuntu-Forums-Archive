---
title: "Kernel panic"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by stewarma101 on 2006-07-09
I have been trying to install ubuntu onto one of my older computers (600mhz, 512mb ram, 128 video...) and the cd boots and the install begins but after 5 seconds the message:

segmentation fault
segmentation fault
segmentation fault
[4294669.42800] not syncing: attempted to kill init!
[4294669.42800] _

The cursor blinks but the computer will not respond only a direct kill will shut it down. 
Could somebody please help me?[-o< [-o<

---

### Post by dmizer on 2006-07-09
humm ... what speed did you burn that disk at?  sometimes you get kernel panic because the disk was burned too fast.  usually between 4x and 8x is optimum.

---

### Post by stewarma101 on 2006-07-09
I burned at 40x (not good)

i just removed all of the extra ram and left a 128 and now the install is initiallizing

---

### Post by nvez on 2006-07-09
It is probably fault RAM.

If the installation finishes at 128MB, plug in another RAM one by one and run memtest86+ until you find the faulty RAM. :)

---

### Post by stewarma101 on 2006-07-09
thanks

---

### Post by stewarma101 on 2006-07-09
> **nvez said:**
> It is probably fault RAM.

If the installation finishes at 128MB, plug in another RAM one by one and run memtest86+ until you find the faulty RAM. :)

How do you run memtest86+?

---

### Post by dmizer on 2006-07-09
when you first turn on the machine it says "loading grub press esc to enter" and it counts down from like 3 or something.  you have to catch it quick.

once you enter into grub, the memtest is avalable for selection.  be forwarned ... memory test takes FOREVER.

---

