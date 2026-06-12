---
title: "Grub Rescue Error- Help!"
date: 2012-10-04
forum: Apple Hardware Users
---

### Post by holdennb on 2012-10-04
Hi,
I'm a pretty new Ubuntu user, and I can't figure out what to do from searching other threads.

Anyway, here's my situation: 
I had Ubuntu 12.04 installed on a partition, and OSX 10.7 on another, and it worked great. Then after I installed 10.8, my Ubuntu partition no longer worked. It gave me:
"error-unknown filesystem 
grub-rescue>"

After doing some reading, I tried to repair grub by booting from a Live USB disk. But now I'm getting the same "grub rescue" prompt when I try to boot from the live usb!

Any ideas?

Thanks a lot

---

### Post by windscape on 2012-10-04
Hi,

I think to get another device to boot on a Mac, you need to hold Ctrl during boot.

---

### Post by raja.genupula on 2012-10-04
look at my signature and find grub restore

---

### Post by doktorOblivion on 2012-10-04
I suspect that when you upgraded Mac OSX it made an update to point to its MBR, which could be on its partition/disk.  You need to go into your BIOS and see if the MAC OSX partition is first in order to boot.  If it is, switch it with the other Ubuntu disk which should have grub on it.  This might work if you have multiple MBRs and the systems on two separate drives.  If they are on a single drive then it could be that MAC overlaid your MBR and no longer points to grub.  There are rescue procedures already defined to recover from this.  Let me know if this is the problem.

---

