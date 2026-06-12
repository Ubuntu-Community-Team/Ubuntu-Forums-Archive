---
title: "Booting up Problems -- GRUB help needed"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by 3rr0r on 2006-09-11
Hi, 

 I was having some trouble setting up my tri-boot system.  My system is configured as follows

/dev/sda1 winxp
/dev/sda2 BackTrack (slax security networking OS)
/dev/sda3 Ubuntu
/dev/sda4 Linux swap file

(i installed them in that order.  xp, backtrack, ubuntu)

Now, it boots up fine to XP and to Ubuntu, but I get this error when trying to boot to BackTrack.

```
VFS: Cannot open root device "current" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

Here is what my fstab looks like:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
#/dev/sda1       /media/sda1     ntfs   defaults,nls=utf8,umask=007,gid=46 0  
/dev/sda2       /media/sda2     ext3    defaults        0       2
/dev/sda4       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


```

---

### Post by mike3k on 2006-09-11
Hit as soon as GRUB starts up to go into interactive mode, select the line for the default boot option & hit E to edit the command. Make sure it specifies the correct root device, and if it isn't specified, add root=/dev/sda3 to the command that loads the Kernel.

Note that GRUB's device names are different:

/dev/sda1 = (hd0,0)
/dev/sda2 = (hd0,1)
/dev/sda3 = (hd0,2)
/dev/sda4 = (hd0,3)
/dev/sdb1 = (hd1,0) ..etc..

Make sure the boot & root commands specify (hd0,2) if your Ubuntu partition is sda3.

---

### Post by 3rr0r on 2006-09-11
> **mike3k said:**
> Hit as soon as GRUB starts up to go into interactive mode, select the line for the default boot option & hit E to edit the command. Make sure it specifies the correct root device, and if it isn't specified, add root=/dev/sda3 to the command that loads the Kernel.

Note that GRUB's device names are different:

/dev/sda1 = (hd0,0)
/dev/sda2 = (hd0,1)
/dev/sda3 = (hd0,2)
/dev/sda4 = (hd0,3)
/dev/sdb1 = (hd1,0) ..etc..

Make sure the boot & root commands specify (hd0,2) if your Ubuntu partition is sda3.

So, will this fix my backtrack booting problems?  I am not sure if you were telling me how to fix the backtrack loading error?

---

### Post by 3rr0r on 2006-09-11
just need confirmation that I need to change the boot screen to show that backtrack should be running off of (0,1) since it is /dev/sda2.   Does that sound right?

---

### Post by jerry_c on 2006-09-11
You may need to edit your menu.lst file. It's in your /boot/grub directory. Your sda2 partion will be hda0,1.

Also, in the future, you may want to consider posting to established related threads rather than trying to start your own. Sometimes it can be pretty lonely waiting for somebody to drop in on your new thread. Here's a thread with a lot of related info:

  [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Good luck.

---

### Post by catlett on 2006-09-11
You need to make a change to your grub menu. Grub is having an issue with your root value for slax. Do this, post your menu
```
sudo gedit /boot/grub/menu.lst
```
Then post this output```
 sudo fdisk -l
```
and this output
```
cat /boot/grub/device.map
```With that info we should be able to fix the issue.

---

### Post by 3rr0r on 2006-09-11
sudo gedit /boot/grub/menu.lst
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		30

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Back|Track (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz root=current 
savedefault
boot

```

sudo fdisk -l
```

err0r@486:~$ sudo fdisk -l

Disk /dev/sda: 79.8 GB, 79826342400 bytes
255 heads, 63 sectors/track, 9705 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1306    10490413+   7  HPFS/NTFS
/dev/sda2            1307        2708    11261565   83  Linux
/dev/sda3            2709        9388    53657100   83  Linux
/dev/sda4            9389        9705     2546302+  82  Linux swap / Solaris

```

cat /boot/grub/device.map
```

err0r@486:~$ cat /boot/grub/device.map
(hd0)   /dev/sda

```

Thank you for telling me what to run in the terminal.  I would have been lost otherwise.  I made my own thread, because I haven't seen anyone else do tri-boot with Back|Track.  Thank you again.

---

### Post by catlett on 2006-09-11
I think I may have your answer. Try changing your BackTrack entry. First open the grub m3enu again
```
sudo gedit /boot/grub/menu.lst
```
Change this entry
```
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Back|Track (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz root=current 
savedefault
```
To this entry
```
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Back|Track (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz root=/dev/sda2 
savedefault
```
I think the only issue is the root parameter was set to current. That doesn't really tell grub anything when it is booting a multiple partition drive. So switching current to the partition BackTrack is on, /dev/sda2, should do it.
Save the file, close it and reboot. Post any error that comes up, if one comes up.

---

### Post by 3rr0r on 2006-09-12
I'm so excited!!! I will try this as soon as I get home and post it to let you know.  It seems like this will be a sound plan  :biggrin:  :mrgreen:

---

### Post by 3rr0r on 2006-09-12
made the change to /dev/sda2 and now I was able to boot up to BT, but the resolution for the first prompt before doing "startx" is huge.  I think I have to go in and edit a file in Backtrack, but not sure.

I am not at least able to boot into Back Track  :grin:

---

