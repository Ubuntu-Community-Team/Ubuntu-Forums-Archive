---
title: "Clock runs fast"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by becominglumberg on 2006-07-25
I know this sounds silly, but my clock currently runs about two minutes fast every day. Were it not so noticable, I wouldn't mind. Also, I always thought that the time was controlled on the motherboard. What gives?

---

### Post by woedend on 2006-07-25
its a bug in the kernel or something.  I fixed it by doing
sudo gedit /boot/grub/menu.lst

find the kernel line, it will have the options on it(something like ro splash)
try adding to that line noapictimer, so that it *may* look something like this

kernel /boot/vmlinuz26 root=/dev/hda1 ro splash noapictimer

make sure you do the first section, not recovery mode.

---

