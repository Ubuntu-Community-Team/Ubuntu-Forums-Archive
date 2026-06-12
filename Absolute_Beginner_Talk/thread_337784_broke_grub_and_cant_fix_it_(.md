---
title: "broke grub and cant fix it :("
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by smile_sunshine on 2007-01-13
Hi,

heres the problem:

1. I got my internet connection back after not having it for 4 weeks so tried to install all the updates, it crashed, 
2. My computer started going really slow and I couldnt fix it so I formatted the partition and reinstalled from a tar bzipped archive of my ubuntu install that i had on another partition (I've done this before with no problems)
3. When I tried to fix grub after reinstalling I can't, so I cant load ubuntu :(

4. I tried :

> mount /dev/hda2 /mnt/linux
chroot /mnt/linux
grub
and got grub prompt

> find /boot/grub/stage1 
gave me > Error 15: File not found


> root (hd0,1)
gave > Error 21: Selected disk does not exist

and > setup (hd0)
gave > Error 12: Invalid device requested

I've mounted the partition and I can see that all my stuff including the menu.1st for grub has copied  OK.

anyone got any ideas please? I cant think of anything else to try :(

thanks :)

---

### Post by sailor2001 on 2007-01-13
for grub problems: download from someone MEMPIS. Hit install center and look for the REPAIR GRUB. MEMPIS is a live disk (unless you want to install as a repair os)

---

### Post by smile_sunshine on 2007-01-13
thanks, will try it :)

---

### Post by smile_sunshine on 2007-01-13
can't find it :( did you mean MEPIS? 
also my hard disk that ubuntu is installed on is starting to go a bit dodgy at times (occasionally it doesnt read some files that are there etc until i reboot - intermittent fault not all the time), could this problem be related to that possibly??

---

### Post by logos34 on 2007-01-13
what about Supergrub?

To check the health of your disk, you can use smart utilities
> sudo apt-get install smartmontools

this installs smartctl

> sudo smartctl -H /dev/hda  
(replace 'hda' with your disk)

---

### Post by smile_sunshine on 2007-01-14
thanks :) fixed it with supergrub, now I'll try smart utilities for checking my hard disk :) thanks

---

