---
title: "GRUB and HDD drive boot order"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by Sutekh on 2005-10-17
Hello,

I installed Breezy yesterday (a real snap) and only came across one issue.  I have 3 drives (!) one IDE HDD for sharing files, and two SATA drives for WinXP and Ubuntu respectively.  In the installer they were designated hda (the IDE), sda (first SATA - WinXP) and sdb (for Ubuntu).

When it came time to install GRUB I told it not to install on the main MBR, but to install on /dev/sdb, the second SATA with the Ubuntu installed on it.  It went away and did it's thing, and I rebooted to see if it worked.  

In my BIOS I set as the priority boot drive the second SATA drive (sdb), and GRUB came up, but when I chose to load Ubuntu I got 

"root(hd2,0) Filesystem type unknown partition type 0x7 ... 
... Error 17: Cannot mount selected partition".

Curious thing is, if I set the IDE drive as the priority boot drive, GRUB loads and I can select Ubuntu or WinXP and they loads no problems.  So I am thinking that when GRUB was installed, the drive boot order was different, and GRUB assigned its device map, etc.  IDE - hda/hd0, SATA#1 - sda/hd1, SATA#2 - sdb/hd2

When I changed the boot order in the BIOS, GRUB didn't know where to look.  I think since the second SATA drive was changed to the first boot device in the BIOS, it became (hd0) not (hd2), where GRUB expected to find Ubuntu. Does this sound correct?  

How would I change the GRUB menu.list and device.map so that I can set the second SATA drive as the first boot??  I think I've almost answered my own question but am unsure.  

Thanks! :)

---

### Post by RickRussellTX on 2005-10-17
Short answer: 

Get into Ubuntu, then edit the file 

  /boot/grub/menu.lst

and make sure that the "root" and "kernel" lines are set correctly, then run 

  grub-install /dev/whatever

where /dev/whatever is the drive you plan to boot from.

---

### Post by Sutekh on 2005-10-17
Thanks for your advice Rick.  

So does GRUB see the order of the drives from the BIOS, ie if IDE is drive # 1 in BIOS, it is hd0 to GRUB, and if SATA is drive # 2 in BIOS, it is hd1 to GRUB, and so on?  

If I changed the BIOS order so that SATA is drive # 2 in BIOS, I will have to change GRUB so that it looks to hd0 instead of hd1, becuase the order has changed, is that right?

Hope that makes sense...

---

### Post by Murgle on 2005-10-17
I believe that it looks at what is master and slave settings (can someone confirm this?) and not the boot priority.  If you change the boot priority it won't matter because grub is only loaded on one drive and if that doesn't boot first you will boot off the other drive.

---

### Post by Sutekh on 2005-10-18
Hmm... all my drives are Master drives, I guess I'll have to have a play when I get home and see what happens... Thanks!

---

### Post by Murgle on 2005-10-18
they might be master but one will be master in the first slot on the motherboard and the other will be master on the second and so forth.

---

