---
title: "Unable to boot Windows"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by psyche@theBrain on 2006-08-14
](*,)  I recently installed ubuntu from winXP and as far as ubuntu is concerned, everything seems to work fine. However, I also want to be able dualboot with windows as well. So, when grub loads, I have selected winXP to boot, but I get an error message "Error 29 Disk write error" and it won't boot. I am using a Toshiba A105 Satellite with intel duo-core proc. 100gb HDD (partitioned 35/55 for win/linux) and the file system for the windows partition is NTFS. Can anyone help? :confused:

---

### Post by il nonno on 2006-08-14
Man, where are all those experts when you need them?

---

### Post by psyche@theBrain on 2006-08-14
Good question. I'm sure someone will get to my question in a little bit though. I only just posted this a little bit ago.

---

### Post by spiral777 on 2006-08-14
Can you post whats in your /boot/grub/menu.list file?

---

### Post by psyche@theBrain on 2006-08-14
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
default		7

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# kopt=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu, kernel 2.6.15-26-686
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-26-686
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title           Windows
rootnoverify            (hd0,1)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```
For any clarification purposes, I have one hdd- windows is on the first partition sda1, and linux is on the second partition, if that helps any.:-k 

PS: I added that last section myself after looking at several other threads in the hopes of solving my problem -though that didn't work](*,) - but the rest I have left alone.

---

### Post by WalmartSniperLX on 2006-08-14
Dude that is very strange really since theyre in diff partitions. When you installed linux did you make sure that you didnt have the windows partition selected in any way at all at the partitioner?? (since by default it shows the partition in the dropdown menu)

---

### Post by psyche@theBrain on 2006-08-14
> **WalmartSniperLX said:**
> Dude that is very strange really since theyre in diff partitions. When you installed linux did you make sure that you didnt have the windows partition selected in any way at all at the partitioner?? (since by default it shows the partition in the dropdown menu)
Yeah I'm pretty sure. Do you have any idea what exactly that error means?

---

### Post by h2gofast on 2006-08-15
The first question is: did you overwrite your windows installation when you installed ubuntu.  Without knowing what you did on the install, there are some possibilities.  Have you ever booted into XP since the ubuntu install?
Is it possible that you formatted the hard drive over the XP install.  It sounds like you repartitioned the hard drive.  
IIRC there is an option to leave the windows partition alone, or to shrink it , and use the remaining disk space for Linux.  
Your grub doesn't look bad except for the stuff you added.  I don't think you need it but I could be wrong.

To check whats on the windows partiton you said was on /dev/sda1
sudo mkdir /winxp
sudo mount -t ntfs /dev/sda1 /winxp
ls /winxp


If the mount command fails give us the output.
If the mount command succeeds give us the output from ls /winxp

Also give us the output of sudo fdisk -l /dev/sda    

Remember the -l in the above command if not just quit fdisk by typing q and pressing enter.

Cheers.

---

### Post by confused57 on 2006-08-15
You can try using the Desktop Live CD to reinstall grub:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Also, your last /boot/grub/menu.lst Windows entry is for booting Windows on a 2nd hard drive...might as well remove it.

If you want to get Windows back:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
(you wouldn't be able to boot Ubuntu, though)

You might want to make a grub floppy beforehand if you decide to repair your mbr with the above method.

[http://www.ubuntuforums.org/showthread.php?t=224345](http://www.ubuntuforums.org/showthread.php?t=224345)
This may enable you to boot Ubuntu with the floppy?

---

### Post by RKCole on 2006-08-15
I will try to offer some advice which may or may not help.  This is what I would try to do in this scenario to see if the Windows partition is still usable (hopefully it is).  I'm only experienced with Linux to a point, so my advice will only go so far...I apologize for that.

1.  Download the Tom's Root/Boot (tomsrtbt) floppy from here: [http://www.toms.net/rb/](http://www.toms.net/rb/)
(I downloaded the tar.gz version)

NOTE:  This is just a bootable floppy which can run a command-line version of Linux.  I've used it in the past on many an occasion with great success. (It's a great tool for techies!)

2.  Extract the file and cd to the new directory.
3.  Insert a formatted floppy disk.
4.  Run the install script in the tomsrtbt directory to create a bootable floppy disk.
5.  Once the new bootable floppy is created, remove the floppy and insert another floppy.
6.  Format the new floppy as FAT32.
7.  Restart the system and boot the tomsrtbt floppy disk and load the OS.
8.  Login to the system. (If I remember right, the password was xxxx)

NOTE:  You are always the root user while using tomsrtbt.

9.  Once logged into the system, remove the floppy disk (as tomsrtbt will remain in RAM memory).
10.  Create two directories in the /mnt directory named floppy and hdd or something which will be appropriate for the drives.
11.  Insert the FAT32-formatted floppy and mount it.
12.  Mount the Windows partition, if possible.
```

mount -t ntfs /dev/hd<WinXP partition> /mnt/hdd

```

NOTE:  This mounts the drive as read-only.  It's typically not safe to write to NTFS partitions, but you can at least copy files out.

13.  If the partition is accessible, copy Ntldr, NTDETECT.COM, and boot.ini to the mounted floppy disk.
14.  Unmount (umount) both drives, leaving the FAT32 floppy still in the FDD.
15.  Restart the computer.

If you were able to successfully copy the files to the floppy, and if the windows partition is still accessible, this disk should boot your Windows XP partition.

Sadly, this is as far as I can help at this moment...I'm still somewhat of a beginner...but I Hope that this will help you in some way, shape, or form.

Good luck!

PS:  I apologize for not putting more detailed code for each step here...I'm eventually planning to write a tutorial for the tomsrtbt disk when I get a chance...but I hope that this can help you in some way.

---

### Post by psyche@theBrain on 2006-08-16
Thank you very much for your replies. However, I'm not sure what exactly happened recently, but now my windows partition is completely unreadable.:shock:  Previously (as in like, yesterday) I had been able to mount my windows partition and be able use it, such as listen to my extensive music library. But, when I rebooted yesterday after installing an update, I was no longer able to access my windows partition- gparted couldn't even recognize the fs type and the freespace on it. Additionally, I couldn't n mount it- I got the following error: 
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
Despite numerous attempts to recover my system to its previous state and undo anything I could have possibly done to cause this disaster, my efforts have been futile. I have unfortunately come to accept that all my data has been lost (unless someone can help[-o< ). This most likely being the case, I have a toshiba recovery disk that would allow me to completely reinstall everything my computer came with- exactly what it should do. The interesting thing is that it allows me to do all this on a pre-existing partition i.e. my current windows partition. 
Therefore, my questions are these:
Does anyone have any ideas on how to recover my windows partition without deleting and starting over? or, if not,
What would I have to do after reinstalling windows to be able dualboot again for both the newly installed windows and the currently existing ubuntu (assuming that when I reinstall windows I won't be able to boot into ubuntu)?
If anyone could point in the right direction that would be a tremendous help

---

### Post by psyche@theBrain on 2006-08-16
Help?:confused:

---

### Post by anaconda on 2006-08-16
What is the output of:

sfdisk -l  /dev/sda

it could just be a corrupted partition table in the end of mbr
there are programs which can search lost partition, or if that isn't possible, then search files from corrupted partitions..

all hope isn't lost...

---

### Post by daou on 2006-08-16
If you have a problem booting into Windows after installing Ubuntu, I recommend you have a look at my post [here]("http://www.ubuntuforums.org/showthread.php?t=237595").

---

### Post by kepos on 2006-08-16
I think that your disk with windows is not healthy. try to check it. it may have some bad sectors or something like that.
if your disk is healthy and if you don't find solution in next few days i would sugest to repair windows instaltion. but not shure will it work.

---

### Post by psyche@theBrain on 2006-08-17
Okay, the output of sfdisk -l /dev/sda is:

Disk /dev/sda: 12161 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+   7222    7223-  58018716    7  HPFS/NTFS
/dev/sda2   *   7223   11925    4703   37776847+  83  Linux
/dev/sda3      11926   12128     203    1630597+   5  Extended
/dev/sda4      12129   12160      32     257040   88  Linux plaintext
                start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda5      11926+  12128     203-   1630566   82  Linux swap / Solaris

From what little that I can tell about this, I would guess that it seems the physical disk partition itself appears to be fine, but does that mean the file directory structure or individual files are corrupt or not- obviously I don't know much about this. Does anyone have any ideas on where I can go from here?

---

### Post by confused57 on 2006-08-17
I really don't know for sure what a solution would be, but you might try:
1.) Repair the Windows mbr by booting up with the Windows install CD(not a recovery cd), press "r" for recovery mode, then enter **fixmbr** and possibly **fixboot**, as described here:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

If this doesn't work, then you "may" need to reinstall Windows to partition #1.

Once you're able to boot into Windows, you can restore grub using the Live CD:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

I wish I could help you more, but these are the only suggestions I can think of...you might want to wait for someone else who may have a better idea.

---

