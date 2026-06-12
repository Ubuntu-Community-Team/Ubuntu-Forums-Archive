---
title: "Error mounting partition"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by oscar78 on 2006-12-19
Hi,

So I have been trying to get my computer configured to boot off of either hard drive, one with windows installed, the other with ubuntu 6.10.  It turns out that the grub wasn't installed on the windows hard drive.  I booted from the ubuntu live cd and installed the grub using the following sequence:   
Code:

sudo grub

This will get you a grub> prompt
Code:

find /boot/grub/stage1

root (hd1,0)

Next enter the command to install grub to the mbr
Code:

setup (hd0)



 When restarting the computer, it takes me to the grub, but I immediately encounter "Error 17: Cannot mount selected partition"

Does anyone have any ideas as to how I could fix this problem?

Thanks

---

### Post by John E on 2006-12-19
Some computers (in fact, many) can only boot from a primary partition if it's on the first physical hard drive.

---

