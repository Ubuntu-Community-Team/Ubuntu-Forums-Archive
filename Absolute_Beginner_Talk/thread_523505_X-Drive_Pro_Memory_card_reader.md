---
title: "X-Drive Pro Memory card reader"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by Pas_sa on 2007-08-12
Hi, I have an X-Drive Pro USB mass storage device. It has an inbuilt 60GB notebook HDD, and a memory card reader built into the side. In Windows XP it works out of the box, with all the memory slots appearing as empty drives in My Computer, cards in there or not.

When I plug it into my system with Ubuntu booted up, it shows the contents of the 60GB drive, but does not let me access any of the memory card slots. I noticed that the 60GB drive is getting /dev/sdc, so I had a look and it has mapped /dev/sdd and others sequentially for the drive but has not mounted them (even though an SD card is inserted).

What can I do to get the SD card drive part mounted? Is there a way I can unmount the X-Drive HDD part, allowing the SD card to work?

---

