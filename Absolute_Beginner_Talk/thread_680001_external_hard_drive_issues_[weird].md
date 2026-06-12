---
title: "external hard drive issues [weird]"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by moonfriedpotatoes on 2008-01-27
hey all. running ubuntu gutsy on a dell d800 latitude.  i have a maxtor one touch usb hdd.  i plug it in, all is well.  i can transfer files to/from it and view/run files on it.  however, when i try to transfer files from my iPod using amarok or gtkPod i get about halfway thru the 80GBs then the drive miraculously ejects itself.  any ideas?  i can't wrap my brain around why it would work great then get pissy and eject.  after it ejects itself, i can't just unplug the usb cable and plug it in again, i have to restart the device manually (unplug/replug the power) then reinsert USB cable, after which it works fine until i try to transfer large amounts of files from my ipod.

---

### Post by dstew on 2008-01-27
Another program to try is [Banshee]("http://www.banshee-project.org/Main_Page").
EDIT: Another thought, is the iPod firmware up-to-date?

---

### Post by moonfriedpotatoes on 2008-01-27
thx fer the reply.  im pretty sure the issue lies in the HDD not in the iPod rip prog or iPod.  the firmware is the latest release tho.... i reformatted the HDD in ext3 format, but now i don't have write permissions except in root.  how do i enable these permissions?

---

### Post by dstew on 2008-01-27
First, you have to make the mount point permissions what you want. Modify permissions with the **chmod **command. If your mount point is /mnt/ext_disk, then, to allow users to read and write, the command would be **chmod u+rw /mnt/ext_disk**. Then, mount the drive with the user and rw options. If you use a command line to mount a partition on the external disk, and if the partition name is /dev/sda1, a mount command would be```
sudo mount -t ext3 -o rw,user /dev/sda1 /mnt/ext_disk
```If it is a usb disk, you might need to check the device name with the **sudo fdisk -l** command, or maybe the lsusb command.

---

