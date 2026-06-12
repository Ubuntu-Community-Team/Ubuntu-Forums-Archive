---
title: "Long time from Power on to GRUB"
date: 2008-02-20
forum: Apple Intel Users
---

### Post by fabietto0102 on 2008-02-20
Hello, 

I am running Ubuntu 7.10 on a MacBook White last generation. Ubuntu is the only OS I have installed as I reformatted the whole disc and start installing Ubuntu from zero. Still, when I switch on the MacBook, it takes good 20 seconds, in which you see a white screen, to get to GRUB and finally load Ubuntu. It's like when you switch on that the computer is searching what OS to load... But there is definitely only one!!

Thank you
Fabio

---

### Post by cyberdork33 on 2008-02-20
> **fabietto0102 said:**
> Hello, 

I am running Ubuntu 7.10 on a MacBook White last generation. Ubuntu is the only OS I have installed as I reformatted the whole disc and start installing Ubuntu from zero. Still, when I switch on the MacBook, it takes good 20 seconds, in which you see a white screen, to get to GRUB and finally load Ubuntu. It's like when you switch on that the computer is searching what OS to load... But there is definitely only one!!

Thank you
Fabio
Unfortunately this is normal though, it doesn't seem to happen to everyone. Apple's EFI searches for GPT disks and bootable partitions for awhile before it gives up and searches for 'legacy' boot methods.

---

### Post by russo.mic on 2008-02-28
My MBP did that too, until I reinstalled OSX.  Now it jumps right to the rEFIt screen.  It used to take almost 30 sec to hit it.

I recommend for more than a few reasons you dedicate 5 gigs or so to an OSX install.  Not only that, but updates and such. 

Good Luck!

Russo

---

