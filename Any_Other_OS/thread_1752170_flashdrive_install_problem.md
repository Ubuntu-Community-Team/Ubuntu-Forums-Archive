---
title: "flashdrive install problem"
date: 2011-05-07
forum: Any Other OS
---

### Post by dkdias on 2011-05-07
I messed up and when I installed Linux Mint 9 (same as Ubuntu) to the flashdrive I had my MBR modified on my harddrive instead of on the flashdrive.  Now when I boot up the computer I get an underscore line in the upper left part of my screen.  If I go into the bios I can tell it to boot to the harddrive and it will go to the OS selection screen. I can then boot into Windows, but it will not boot into linux on that particular screen. Actually it won't let me boot into the flashdrive at all.  Please help!!  I tried to restore my Windows Vista OS to an earlier date (I was hoping it would restore my old MBR), but that did not work. What I want it to do is boot up to linux on the flashdrive when the flashdrive is installed or boot up to Vista on the hard drive when the flashdrive is not installed. Thank you for your help!!

---

### Post by lmarmisa on 2011-05-07
Try this link for reparing your MBR:

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by Perfect Storm on 2011-05-07
Moved to Other OS/Distro Talk.

---

### Post by ventrical on 2011-05-08
I always try to make it a rule to install a LInux distro to a pen-drive WITHOUT the hardrive installed. This way I get a clean and perisitive boot. Then, after I install the harddrive I can update ( do not update on flash drive until install is done).

  The updater has a way of interfacing with the GRUB bootloader and after all of the updating is done you will get a rock-solid GRUB boot screen.

**Some PCs will just not boot from USB with the hardrive in. Dell PCs are perfect as well as some Acers. You can adjust the settings in BIOS but, unless the BIOS is updated here is just no way unless you use the PLOP bootloader.

---

### Post by dkdias on 2011-05-08
> **ventrical said:**
> I always try to make it a rule to install a LInux distro to a pen-drive WITHOUT the hardrive installed. This way I get a clean and perisitive boot. Then, after I install the harddrive I can update ( do not update on flash drive until install is done).

  The updater has a way of interfacing with the GRUB bootloader and after all of the updating is done you will get a rock-solid GRUB boot screen.

**Some PCs will just not boot from USB with the hardrive in. Dell PCs are perfect as well as some Acers. You can adjust the settings in BIOS but, unless the BIOS is updated here is just no way unless you use the PLOP bootloader.

To install on a laptop with a pen-drive, would unmounting the harddrive work the same as disconnecting the harddrive? To get a clean install? I would not know how to disconnect a harddrive on a laptop.... ..

---

