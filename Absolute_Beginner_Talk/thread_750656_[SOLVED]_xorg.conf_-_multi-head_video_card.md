---
title: "[SOLVED] xorg.conf - multi-head video card"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by anewguy on 2008-04-09
If your nvidia graphics card has a "normal" vga jack, a HDMI jack and a svideo jack, do you have to do something special to xorg.conf so it knows you only want the vga jack enabled?

Will this make a difference in a "device not found" error ?

Thanks! :)

---

### Post by gsmanners on 2008-04-09
I'm pretty sure that VGA is the default.

---

### Post by anewguy on 2008-04-11
Problem "solved" for now - problem was the old Biostar M6TZA (AGP 1.0) motherboard I'm using doesn't allocate the video card via the BIOS correctly.  No fix for this motherboard, but problem at least solved.  My "new" (used KT7-RAID) motherboard recognized the card just fine and the restricted driver as well as the nVidia driver (1 back) worked fine.  Unfortunately the motherboard shot craps after about an hour.  :)

---

