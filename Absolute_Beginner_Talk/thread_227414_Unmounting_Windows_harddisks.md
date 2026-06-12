---
title: "Unmounting Windows harddisks"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-08-01
Ok, i've just installed Ubuntu (second time) but this time it has mounted all of my windows harddisks, is there a way I can unmount them?

Calv

---

### Post by Orestes on 2006-08-01
This works on virtually any Linux distro, though I haven't tried it on Ubuntu:

sudo gedit /etc/fstab

(type your password)

find any reference to the windows partitions (clue: the most likely Windows partition is /dev/hda1) and make the first character of that line a # (US: pound, UK: hash) to disable it.

Reboot and see what happens!

Good luck.

---

