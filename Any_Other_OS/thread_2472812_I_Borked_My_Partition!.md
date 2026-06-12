---
title: "I Borked My Partition!"
date: 2022-03-13
forum: Any Other OS
---

### Post by J._D._Trouteater on 2022-03-13
Hi, while getting way over my head and using parted on LibreElec, I completely erased two partitions on a 4TB external USB hard drive. My fault!

I was able to use testdisk to get the one back, but it seems like a small partition at the beginning is missing? I am kinda out of my element here, but hopefully putting the small (perhaps boot?) partition back will make the USB hard drive work again?

Anyway here's a screenshot of my gparted. If anyone can help me I would really appreciate it!

[ATTACH=CONFIG]290146[/ATTACH]

[ATTACH=CONFIG]290147[/ATTACH]

---

### Post by QIII on 2022-03-13
Moved to ***Any Other OS***

---

### Post by J._D._Trouteater on 2022-03-13
Thanks. That’s fine to move my question, and I am using gparted in Ubuntu if that makes any difference. &#8234;¯\_(&#12484;)_/¯&#8236;

---

### Post by oldfred on 2022-03-14
Please attach screen shots, not post in line. 
Easy to attach with Forum's Go Advanced editor and paperclip icon.

Since large drive it needs to be gpt. In gparted open the left side window. view, device info
Or better show this:
sudo gdisk -l /dev/sdc

When using testdisk you have to specify whether MBR(msdos) or gpt to get correct partition recovery.

---

