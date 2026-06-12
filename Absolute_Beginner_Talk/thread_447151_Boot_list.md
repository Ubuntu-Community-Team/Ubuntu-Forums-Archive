---
title: "Boot list"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by AlecWest on 2007-05-17
My current system runs a dual-boot (Win98SE and WinXP).  And when I boot up, I'm given a choice of one or the other.  Today, I installed Ubuntu 7.04 on a free partition.  How to I get Ubuntu added to the choice menu at boot-up ... or can I get it added?  If not, how do I boot-up Ubuntu from its partition?

---

### Post by kittyhawk63 on 2007-05-17
You might try adding this to your /boot/grub/menu.lst
Start Applications->Accessories->Terminal
Copy and paste: gksudo gedit /boot/grub/menu.lst
Type in your password when asked.
Then go to where you see:
## End Default Options ##

And copy and paste in the following:

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=e4c0c499-7c09-4920-8747-212ecb7a598e ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=e4c0c499-7c09-4920-8747-212ecb7a598e ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

---

### Post by Quintin Riis on 2007-05-17
Google for "boot.ini linux".

I would recommend installing GRUB instead of using the NT boot loader though.  Google for "grub howto" or so for more details.  

I should think that the Ubuntu installer would've put GRUB on and made entries for Windows.

---

### Post by k33bz on 2007-05-17
are you able to get into your Ubuntu partition?

---

### Post by AlecWest on 2007-05-17
> **k33bz said:**
> are you able to get into your Ubuntu partition?
Using WinXP, I can see the structure with my Partition Magic software.  Outside of that, I'm uncertain how to get into the partition with any kind of tool.

---

### Post by k33bz on 2007-05-17
Then i would do exactly what Quitin said to do. Doesnt seem like your computer is recognizing that you have a 3rd OS on your system

---

### Post by AlecWest on 2007-05-17
Thanks for everyone's help.  Because of my weird work schedule, "my weekend" concludes tonight ... so I'll probably have to retry the install on my next weekend.  But, I don't give up (grin).  As a Nepalese monk once told Tom Selleck, "The oxen are slow, but the Earth is patient."

---

