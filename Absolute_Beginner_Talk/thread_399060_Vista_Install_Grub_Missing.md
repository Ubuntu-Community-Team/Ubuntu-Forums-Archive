---
title: "Vista Install Grub Missing"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by filam on 2007-04-01
I had my laptop partitioned into two parts, Ubuntu 6.10 and Windows XP. I recieved a Vista Business disc and installed it to a third partition. On restart Grub is replaced by a Microsoft loading screen, with "Vista" and "An older version of windows" as options to boot into. The third Ubuntu partition clearly still exists. How can I boot into Ubuntu (add it to the current boot screen) or replace it with Grub? (without reinstalling ubuntu?) Thanks.
P.S. Vista Business is extremely lame. I can't wait to boot back into Ubuntu.

---

### Post by bigee1212 on 2007-04-01
try getting the super grub disk iso and re installing grub

---

### Post by calraith on 2007-04-01
You could also boot into your Ubuntu installer CD and do the following in a terminal window:

mount -t auto /dev/hda1 /target  (or hda2 or sda5 or whatever your / partition in Ubuntu is)
chroot /target
grub

Then at the grub prompts:
find /boot/grub/stage1
root (hd0,0)   (or whatever the output of the find command was)
setup (hd0)
quit

then exit, exit, reboot.  Voila!

---

