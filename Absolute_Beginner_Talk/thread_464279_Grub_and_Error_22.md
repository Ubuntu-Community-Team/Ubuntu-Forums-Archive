---
title: "Grub and Error 22"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by BuddhaBubba on 2007-06-04
machine details:
amd64 3800+
1 gig RAM
Asus A8N32-SLI Series
IDE HD1 has Vista, IDE HD2 has XP Home
SATA 1 has programs and the Ext3 partition of Linux and a 2gb Linux swap partition
pci-express nvidia 7600gs video card with 256mb vram

So, I installed ubuntu 6.10 32-bit just to be on the safe side because I heard there were problems with the 64-bit

But when I restarted I got the following message
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 22

and then it stays that way...any help? :(

---

### Post by jonward0690 on 2007-06-04
Well you are going to have to reinstall grub from the live cd

---

### Post by BuddhaBubba on 2007-06-04
> **jonward0690 said:**
> Well you are going to have to reinstall grub from the live cd

you mean I can just reinstall GRUB instead of the whole system?

for a little more info, these are some of the error messages I get before I even get to the installation:
ex:
[ 208.149815] hdc: ide_intr: huh? expected NULL handler on exit
[ 208.198624] Buffer I/O error on device hdc, logical block 353612
these two messages repeat more than 10 times before ubuntu loads

as a side note:
I think it's ironic that Ubunut<sic> works near-perfectly on my proprietary Dell Inspiron 9300 while on my Generic AMD64 machine it dies :haha:

---

### Post by dexter.lives on 2007-06-04
I finally got my system to dual boot a couple weeks ago after wrestling with the same problem.  I fixed it by making the HD with Ubuntu the master, and the XP hard drive the slave.  Then I followed the directions **[B][here.]("http://ubuntuforums.org/showthread.php?t=179902")  **[/B]

I hope this works for you.  Good luck.

---

### Post by BuddhaBubba on 2007-06-04
> **dexter.lives said:**
> I finally got my system to dual boot a couple weeks ago after wrestling with the same problem.  I fixed it by making the HD with Ubuntu the master, and the XP hard drive the slave.  Then I followed the directions **[B][here.]("http://ubuntuforums.org/showthread.php?t=179902")  **[/B]

I hope this works for you.  Good luck.

thanks.  instead of switching around the hard drives, I am currently resizing the master HD with a linux partition and installing it on there... see if that works

---

### Post by BuddhaBubba on 2007-06-04
just an update
...
once I installed ubuntu on my master HD it worked (and windows is even still accessible!)

so, to delete the 'dead' installation i just delete the entry out of /boot/grub/menu.lst and then delete the partition that the 'dead' linux is on, right?

---

