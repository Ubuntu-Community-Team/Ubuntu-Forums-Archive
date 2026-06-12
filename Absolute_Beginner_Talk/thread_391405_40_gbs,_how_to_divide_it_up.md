---
title: "40 gbs, how to divide it up?"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by denbeau on 2007-03-23
I have a computer with a 40gb harddrive. I wanted to install Ubuntu, and PCLinux.
I wanted to learn more about Ubuntu and PCLinux, so I can be free of M$ someday! 
Is this possible? Which should I do first? 
Thanks 
Denbeau

---

### Post by swamytk on 2007-03-23
1. Any one can be installed first.
2. For Ubuntu you won't need more than 10GB root partition approx. But PCLinuxOS installs a lot of stuffs by default, so try to give around 20GB atleast as root partition. Leave 1GB as swap. Rest can be /home partition. 
3. When you install second linux, install the Boot record on root partition, and copy the corresponding grub entry lines to first installed /boot/grub/menu.lst file.

---

### Post by tallman9 on 2007-03-23
swap is better to be the last partition, and creating a partition apart for /boot is another good idea :)

---

### Post by denbeau on 2007-03-23
Ok I'll give it a whirl! 
Swamytk, I'm not sure about your #3. suggestion. Maybe it will be apparent as I install them. 
Thanks.

---

### Post by Mateo on 2007-03-23
I wouldn't recommend creating a lot of seperate partitions for sharing and such, it adds up to a lot of wasted space because partitions are not flexible.

---

