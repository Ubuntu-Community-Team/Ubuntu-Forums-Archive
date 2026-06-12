---
title: "can i do hard disk 2 hard disk copy of ubuntu"
date: 2005-09-11
forum: Absolute Beginner Talk
---

### Post by vinthalie on 2005-09-11
i have lan network but i want to copy it to from other computer, do hard disk  copy can help, because i used ubuntu now and i download a lot of patches,  packages and it took me more than 8 hours.. ty

---

### Post by lompolo on 2005-09-11
If You can change hard drive from destination computere to source computer or vice versa, 


Both hard disks must be unmounted. Live-cd is easy way doing this.
something like this in terminal: dd if=/dev/hda of=/dev/hdb bs=1M

if=input file of= output file bs=block size

try dd --help in terminal for more information

Correct this if I am wrong.

---

