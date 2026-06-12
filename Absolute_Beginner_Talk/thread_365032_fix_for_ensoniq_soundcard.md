---
title: "fix for ensoniq soundcard"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by platypuss72 on 2007-02-19
i have found the fix  :-D :-D :-D :-D :-D 
after a week of hunting and help on forums i found this and it works 


 Re: Ensoniq 5880 No Sound
Hi all!!

Did you tried adding "acpi=ht" to your GRUB/LILO?

I was like you, trying to "hear something" from my box, but nothing at all, searching and testing all the answers I've found... until I made the next modification of GRUB (that I read about a shutdown problem):

(extract from my /boot/grub/menu.lst)

title Ubuntu, kernel 2.6.15-25-386
root (hd1,0)
kernel /boot/vmlinuz-2.6.15-25-386 root=/dev/hdb1 ro quiet splash vga=788 acpi=ht
initrd /boot/initrd.img-2.6.15-25-386
savedefault
boot


... and now I can hear my music, videos, system sounds ...

from here ... [http://ubuntuforums.org/showthread.php?t=140604](http://ubuntuforums.org/showthread.php?t=140604)



many many thanks luke

---

