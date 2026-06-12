---
title: "return to windows"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by polypeter on 2008-02-29
I have a new  laptop with Ubuntu on it, and ubuntu works nicely. However I am not really happy with the computer, and want to exchange it for another one (or resell if this doesn't work). To do this I think it's best to put a clean installation of windows back on the computer. I have the recovery disk with Windows Vista on it, but I'm not sure how to reinstall windows. On other threads it just says 'boot from the windows disk' but I don't know how to do this. When I press esc when the computer starts up I get a menu with various versions of ubuntu to choose from, but none saying 'boot from disk'. So how do I get windows back?

Basically, Ubuntu was installed clean, just ubuntu with no partitions on the hard drive. I have the windows vista recovery dvd, but i don't know how to boot from it in order to restore windows.

Be really grateful for some advice!

---

### Post by sstusick on 2008-02-29
Put the Windows Vista recovery DVD in the DVD-ROM drive and reboot the computer. Go into your BIOS, as soon as the computer starts up, you can get into BIOS by hitting 1 of the following keys, depending on the manufacturer: F1, F2, F10, DEL and adjust the boot order of the devices, make sure your DVD-ROM drive is first in the boot order. Then save your changes and reboot once again, and this time the computer should boot up from the Vista recovery DVD.

---

### Post by taurus on 2008-02-29
Put Ubuntu CD and boot from it.  If it doesn't boot from the CD (which is impossible since you need to boot from it to install Ubuntu), go into the BIOS and make sure you have the CDROM as the first bootable device.  Then, open gparted in System -> Administration and delete all the partitions on your harddrive.  If there is a lock on the swap partition, shutdown down gparted first and unmount the swap with

Applications -> Accessories -> Terminal
```
sudo swapoff /dev/sda5
```
Or whatever the swap partition is.  Now, fire up gparted again and delete everything.  Then, format that harddrive to ntfs.  Reboot and insert your Vista recovery disc and follow the directions on screen to reinstall Vista.

---

