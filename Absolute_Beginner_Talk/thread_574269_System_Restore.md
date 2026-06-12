---
title: "System Restore"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by TaiQui on 2007-10-12
I have an Acer aspire 5570Z and I want to restore to the factory default with vista. The only reason I do is because I actually put ubuntu over vista on accident. Now I want to dual boot, and to make sure I'll just use  Wubi. SO is there a way to restore it back to Windows Vista

---

### Post by MinstrelBoy on 2007-10-12
This may work .....

Hidden partition main page
Press <Alt> + <F10> during POST to boot the system from the hidden hard disk drive
partition and access the hidden partition main page.

---

### Post by TaiQui on 2007-10-12
Checking...

EDIT: It doesn't work..

---

### Post by TaiQui on 2007-10-12
bump.

---

### Post by MinstrelBoy on 2007-10-12
From the 5570Z user manual

[http://support.acer-euro.com/drivers/notebook/as_5570.html](http://support.acer-euro.com/drivers/notebook/as_5570.html)

I want to restore my computer to its original settings without recovery CDs.

             Note: If your system is the multilingual version, the operating
             system and language you choose when you first turn on the
             system will be the only option for future recovery operations.

This recovery process helps you restore the C: drive with the original software
content that is installed when you purchase your notebook. Follow the steps
below to rebuild your C: drive. (Your C: drive will be reformatted and all data
will be erased.) It is important to back up all data files before using this option.

Before performing a restore operation, please check the BIOS settings.
1     Check to see if Acer disk-to-disk recovery is enabled or not.
2     Make sure the D2D Recovery setting in Main is Enabled.
3     Exit the BIOS utility and save changes. The system will reboot.
             Note: To activate the BIOS utility, press <F2> during POST.
  English
          48
          To start the recovery process:
          1    Restart the system.
          2    While the Acer logo is showing, press <Alt> + <F10> at the same time to
  enter the recovery process.
3 Refer to the onscreen instructions to perform system recovery.
                      Important! This feature occupies up to 10 GB in a hidden partition
                      on your hard disk.

---

### Post by TaiQui on 2007-10-12
Doesn't work.... It ignores it when I press Alt+F10

---

### Post by Frak on 2007-10-12
Did you choose "Write to entire disk" by any chance?

---

### Post by TaiQui on 2007-10-12
Yes... I think so.

---

### Post by Frak on 2007-10-12
I'm not very clear on Hidden Partitions, but there is a chance that Ubuntu took control of the disk and overwrote everything.

---

### Post by Duck2006 on 2007-10-12
From the live CD in the terminal type

fdisk -l

and post the output that will show you if the recovey partition is still there.

---

### Post by TaiQui on 2007-10-12
This is what I got...

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...

---

### Post by Duck2006 on 2007-10-12
sorry that sould have been

sudo fdisk -l

---

### Post by TaiQui on 2007-10-12
Ok. I got this.

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf688bdad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18704   150239848+  83  Linux
/dev/sda2           18705       19457     6048472+   5  Extended
/dev/sda5           18705       19457     6048441   82  Linux swap / Solaris

```

---

### Post by Duck2006 on 2007-10-12
Ok so all you have on that drive is ubuntu. NO windoze just linux from what fdisk shows

---

### Post by TaiQui on 2007-10-12
Yeah.... so I can't restore? :(

---

### Post by Duck2006 on 2007-10-12
No you can't restore from the hard drive. The only way is you will have to get a copy of windows or a restore cd from acer.

---

