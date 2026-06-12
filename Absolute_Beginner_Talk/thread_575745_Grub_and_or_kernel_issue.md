---
title: "Grub and or kernel issue"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by usarmykr on 2007-10-14
OK, here is my issue.  I fresh installed kubuntu after trying a few other distros.  I login for the first time and have about 200mb of updates to download.  After the system is done updating I install my graphics driver.  I reboot, and I get auto booted into recovery mode (a black screen where I can type, but things like "startx" don't respond) OK, I reboot, and hit esc to get into grub.  I select recovery mode, and get booted  into kubuntu.  Anyone know why I am getting autobooted into recovery mode?  I saw one site about the kernel update sometimes messing it up, but dont know how to fix it.

---

### Post by Shazaam on 2007-10-14
Please post  copies of 
```
sudo fdisk -l
```
(small L) and your  menu.lst (small L) here.

---

### Post by ajgreeny on 2007-10-14
>   I select recovery mode, and get booted  into kubuntu.Do you mean you get to the normal login screen and start as the user you wanted?  If so it sounds as though your /boot/grub/menu.lst file has become confused, (either that or I have!).  Let's have a look to see what it contains and we may be able to help.

---

### Post by usarmykr on 2007-10-14
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29644   238115398+  83  Linux
/dev/sda2           29645       30401     6080602+   5  Extended
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris

and heres the menu.lst

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=bde1f615-7c05-4366-bf6f-8df10312b9d7 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=bde1f615-7c05-4366-bf6f-8df10312b9d7 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=bde1f615-7c05-4366-bf6f-8df10312b9d7 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=bde1f615-7c05-4366-bf6f-8df10312b9d7 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


Heres another question, seems dumb to ask but, installing games, whats the typical directory, not sure how the partitions ares etup vs windows lettered drives, is "home" my main big data area?

---

### Post by Shazaam on 2007-10-14
I need to see your versions of this-
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0


and this-
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

please.

---

### Post by usarmykr on 2007-10-14
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0



and


## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=bde1f615-7c05-4366-bf6f-8df10312b9d7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

---

### Post by Shazaam on 2007-10-14
Hmm. Seems fine or I am missing something. Anyone else have an idea?

---

### Post by usarmykr on 2007-10-14
Far as I can tell all that is happening is it is booting me into tecovery mode instead of regular.  Its solved by just hitting esc and selecting the recovery mode, which boots me into kubuntu, but selecting the regular mode boots me into recovery.

---

