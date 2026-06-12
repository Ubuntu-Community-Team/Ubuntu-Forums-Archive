---
title: "&quot;Error Loading Operating System&quot;: 9.10 Macbook Pro"
date: 2009-11-13
forum: Apple Hardware Users
---

### Post by Who on 2009-11-13
Hi,

I have just installed 9.10 on my Mac, but I can't boot it. I know it is on there and working because when trying to debug I booted from the Ubuntu CD and chose 'Boot from First Hard Disk' - and Ubuntu booted (via GRUB). When I boot while holding alt I get an option between Macintosh HD and 'Windows' - selecting Windows gives me "Error Loading Operating System"

I have 4 partitions. 
1. Efi
2. Os X
3. Ubuntu
4. Windows (not yet installed/blank partition)

I made sure that in the Ubuntu installer I put Grub on sda3, i.e. the root Ubuntu disk.

I _have_ used rEFIt to resycn and that just broke my ability to boot Ubuntu using the Ubunut CD as described above. 

When I boot (holding alt) I _only_ see two options: Macintosh HD and 'Windows' - selecting Windows shows me 'Error Loading Operating System' - I am suspicious that this is actually trying to find something on the empty Windows partition.

I have tried sudo bless --device /dev/disk0s3 --setBoot --legacy

to no avail

rEFIt _also_ only recognises two partitions to boot from, and just hangs on the grey screen with windows icon if I select the only non OS X Option

So - any ideas what's wrong and how to troubleshoot or fix it?

---

### Post by Who on 2009-11-15
I installed 9.04 and then upgraded to 9.10 (which means that I'm using grub1, not grub2) and it works fine.

Why was this necessary?

---

### Post by aprigiosimoes on 2009-11-16
problems?

install ubuntu and then enter the live cd of ubuntu open console and mount the partition that ubuntu is installed and use chroot to enter the partition.

mount / proc and install grub 1 (grub or grub-legacy) and run grub-install / dev / HARD OR update-grub

and reboot.

---

