---
title: "ntfs-config error"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by Vanish00 on 2007-08-03
I installed ntfs-3g so I can write & delete flies off my windows partition.  Once I check off "Enable write support for internal device" and click ok.  I get this error....

----------------------------------------------------------------------------------------------------------------------
ERROR:
Mounting /media/sda1 failed.

Volume is scheduled for check. Please boot into Windows TWICE, or
use the 'force' mount option. For example type on the command line:

    mount -t ntfs-3g /dev/disk/by-uuid/0C48DCE648DCD016 /media/sda1 -o force

Or add the option to the relevant row in the /etc/fstab file:

    /dev/disk/by-uuid/0C48DCE648DCD016 /media/sda1 ntfs-3g defaults,force 0 0
-----------------------------------------------------------------------------------------------------------------------

Any know how I can write to my NTFS partition?

---

### Post by NAT1V3 on 2007-08-03
is windows in hibernation?

---

### Post by Vanish00 on 2007-08-03
> **NAT1V3 said:**
> is windows in hibernation?

Nope, I have my system setup for a dual boot.  Right now i'm in Ubuntu.

---

### Post by NAT1V3 on 2007-08-03
what i mean is did you hibernate windows and boot into Ubuntu

also try running chkdsk on your windows partition

---

### Post by Vanish00 on 2007-08-03
> **NAT1V3 said:**
> what i mean is did you hibernate windows and boot into Ubuntu

also try running chkdsk on your windows partition

When I was in windows earlier I just hit the restart and picked Ubuntu from the GRUB.  I can run a chkdsk on the windows partition.  Do you know if Gparted has a check disk feature?  if not what do you use or recommend i should use?

---

### Post by NAT1V3 on 2007-08-03
log in to win xp win key+R -> cmd -> type in "chkdsk :c /f" then reboot select windows from grub let the check run shut down win the back to ubuntu and try to mount again

also i find when stuff like this happen open up NTFS config deselect internal drives, right click on the (c:) drive in nautilus/konqueror select mount the reselect internal drives and see if it mounts but in your case i think its the 1st solution

good luck

---

### Post by Vanish00 on 2007-08-03
Your right NAT1V3, that check disk did the trick.  I guess I never logged back into windows after I installed ubuntu because as soon as I was loading up windows it prompted me to perform a check disk.  Thanks!

---

