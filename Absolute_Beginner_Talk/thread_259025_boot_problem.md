---
title: "boot problem"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by jacmac101 on 2006-09-16
New to Linux, downloaded Ubuntu 6.06 kernal 2.6.15-26-386, and burned the .iso file to disk.  Booted the CD and tried out some of the features of the Desktop and such, liked what I saw and installed to a 250 GB HD I had free of files. Removed the CD and booted through grub to the new installation. Setup my preferences, my email, and then re-booted. Loaded all the drivers, and then stopped with the following messages:

" Alert! /dev/hdf2 does not exist. Dropping to shell"
" /bin/sh: can't access tty; job control turned off"

Leaving me in BuzyBox v1.01
I can only boot from the CD
Any help would be appreciated

System Specs:  Gigabyte GA-K8NS Pro (nForce3 250 chipset)
               AMD Athlon XP64 3400+
               2 GB DDR P)C 3000 ram
               4 250 GB various make HD's
               2 on GigaRaid IT8212, set up as mstr/slave
               ATI Radeon X850 XT 250 MB ram
               1 Combo drive DVD/CDR
               1 Combo drive DVDR/CDR
               Various USB, and Wireless devices

---

### Post by bernied on 2006-09-16
/dev/hdf2 is the second partition on the fifth disk. Since you say you only have four, and two of them are on a RAID, this seems to be a mistake by the installer.

The file you want to edit is called menu.lst and it will be located in the /boot/grub/ directory of the partition that you installed ubuntu into.

The line you want to change will begin with 'kernel' and somewhere in it will be 'root=/dev/hdf2', which you need to change. This line tells the bootloader (grub) the name of the kernel to load, and the boot options to pass to it. That 'root=' is the boot option that tells the kernel where all its files are.

You will need to find out what device your ubuntu install is on, and change the /dev/hdf2 to the correct location.

You should be able to reach the menu.lst file from the live-cd. If you can find the file from the list of disks on the desktop you will be halfway there.

...

---

### Post by bernied on 2006-09-16
So if you can find the file in a file manager, open a terminal (I think that's in the System menu, then Terminal), and type:
```
mount
```
That should give you a list of mounted devices and your ubuntu install should be on one of them. See if you can find the entry that corresponds to the text in the title-bar of your file manager that's listing the menu.lst file. If you can then you've found the device. Here's what some of mine looks like:
```
/dev/hdb5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
/dev/hdb2 on /boot type ext2 (rw)
/dev/hdb6 on /media/storage type vfat (rw,utf8,umask=002,gid=100)
```
So the bit on the left is the name of the device, and the bit after 'on' is the location on the filesystem where it is mounted. So, say you worked out it was the bottom entry that was the location of your ubuntu install, 'root=/dev/hdb6' would be the right option for the kernel line. And, to edit the menu.lst file you'd type:
```
sudo nano /media/storage/boot/grub/menu.lst
```
(sudo means run as root user, nano is the editor)

You can also use the commands:
cd - change directory
ls - list files and directories in a directory
less - list the contents of a file

In my opinion, which isn't worth that much, the ubuntu installer probably had trouble interpreting your  complicated disk setup. The developers would probably like to know about your situation.

Welcome to linux!

---

### Post by bernied on 2006-09-16
Just re-read your first post - curious that it booted the first time ok.
Can you post the output from:
sudo fdisk -l

---

