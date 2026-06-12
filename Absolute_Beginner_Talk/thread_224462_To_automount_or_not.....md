---
title: "To automount or not...."
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by Anduu on 2006-07-28
I have 3 CD/DVD drives...a CDRW,DVDRom and an external usb dual layer DVDRW...

Should I let Ubuntu do its thing and let it automount my CD/DVD drives or should I mount them via my fstab?

I dunno...my only logic for using fstab is it may free Ubuntu up a bit by not having to figure them out on its own...or am I just splitting hairs here?

Any thought/opinions?

---

### Post by mlind on 2006-07-28
I'm not sure how automounter thigy works, but I've got my DVD burner and reader on /etc/fstab. It seems that this automounter respects these entries, so you can use /etc/fstab entries to control where devices are actually mounted.

---

