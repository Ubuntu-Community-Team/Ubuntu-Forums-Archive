---
title: "GRUB error 13 when I try to boot XP"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by marmaladejackson on 2007-02-03
Hi all~

Just got the first successful install of ubuntu going... hooray!  But I get:

"Error 13: Invalid or unsupported executable format" 

whenever I try to boot XP from GRUB.  is there anyway for me to get back to XP?  Please don't tell me I pooched it! 

I got tow hard drives, I tried to make one a pure XP drive and the other a pure ubuntu drive.  If I set the ubuntu drive as #1 in the bios, the GRUB will start but nothing will load (kernel panic).  If I set the XP drive as #1, I get GRUB and ubuntu shortly after, but whenever I trt to boot XP I get the Error 13...  I really hope I didn't pooch the MBR.

Any suggestions?

Thanks much!
Brian

---

### Post by danielph on 2007-02-03
[B]Grub Error 13:

13[/B] : **"Inconsistent filesystem structure"** This error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects.  This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB.

Can you post your ```
/boot/grub/menu.1st
```

---

### Post by igknighted on 2007-02-03
For some reason grub can be finicky with the Windows bootloaders... I get the same error when I point grub to my vista boot loader (luckily they are on seperate HD's so I can select the disc to boot via the bios, but its a little annoying).  If anyone has a good fix for this please post it.

---

### Post by marmaladejackson on 2007-02-03
Thanks... Is this what you are looking for?


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
# kopt=root=UUID=67493ccf-bd5b-4482-84b8-971418203520 ro
# kopt_2_6=root=/dev/sdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc1.
title		Ubuntu 6.10 (6.10) (on /dev/hdc1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by marmaladejackson on 2007-02-03
knighted...
I am also using 2 HD's and I had also planned on switching them thru the BIOS, but no matter which one I pick, it goes to GRUB.  Setting my "linux" drive as boot # 1 allows me to load ubuntu no problems.  Setting my "XP" drive as number one doesn't get any farther than the GRUB.  Errors 17, 13, or kernel panic.

---

### Post by igknighted on 2007-02-03
> **marmaladejackson said:**
> knighted...
I am also using 2 HD's and I had also planned on switching them thru the BIOS, but no matter which one I pick, it goes to GRUB.  Setting my "linux" drive as boot # 1 allows me to load ubuntu no problems.  Setting my "XP" drive as number one doesn't get any farther than the GRUB.  Errors 17, 13, or kernel panic.

Thats odd... although, it looks like you have multiple linux installs, so maybe one installed grub to one MBR, while the other installed to the other one.  For me, grub is on sda (hd1) while windows bootloader sits on hda (hd0), so I can choose via bios.  I would rather just use grub however.  Does your windows boot from grub OK?

---

### Post by danielph on 2007-02-03
Grub is normally installed to the MBR on the disk you are booting from. There is a pointer if you like to where it will find the /boot folder - normally /boot.

I would tend to have grub installed on the MBR for the first disk and that disk running Ubuntu. This is the disk you are booting off.

From your menu.1st file you have 2 installs of Ubuntu listed.

Can you post ```
sudo fdisk -l
``` and ```
ls -l /boot 
``` and I'll try and work it out. I am no expert, but I have played around with grub a fair bit.

---

### Post by igknighted on 2007-02-03
FWIW, I did manage (through trial and error of changing the partition Grub was pointed to) to get Vista to boot through grub.  Marmalade... try the switch i suggested, and if that doesnt work boot to grub and hit 'e' to get into edit mode and you can just keep trying different combinations until you find the proper one.  Trial and error has never failed me with grub :)

---

### Post by marmaladejackson on 2007-02-03
Dan an Knight...
Thanks for the help there... fell asleep.  No, windows will NOT boot.  I have attempted installing ubuntu multiple times, mabe that's why it seems there are two versions installed.  This was actually the first time I was able to make it past the GRUB.  So are you guys thinking that if I play around with the HD location of the windows partition, I'll eventually find it ((hd0,0) perhaps)?  I'll try and get those other screen shots to ya, but I am a real noob and my productivity has dropped to 0.

thanks again!

---

### Post by marmaladejackson on 2007-02-03
brian@brian-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda2           10200       30400   162264532+   f  W95 Ext'd (LBA)
/dev/sda5           10200       20398    81923436    7  HPFS/NTFS
/dev/sda6           20399       30400    80341033+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18706   150255913+  83  Linux
/dev/sdb2           18707       19457     6032407+   5  Extended
/dev/sdb5           18707       19457     6032376   82  Linux swap / Solaris

Disk /dev/hdc: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9328    74927128+  83  Linux
/dev/hdc2            9329        9726     3196935    5  Extended
/dev/hdc5            9329        9726     3196903+  82  Linux swap / Solaris
brian@brian-desktop:~$ 

Well, I guess at least you can see the NTFS partition still intact on the 250 giger... That's a good sign I guess.

---

### Post by marmaladejackson on 2007-02-03
brian@brian-desktop:~$ ls -l /boot
total 8860
-rw-r--r-- 1 root root  282323 2006-12-05 13:21 abi-2.6.17-10-generic
-rw-r--r-- 1 root root   67417 2006-12-05 12:37 config-2.6.17-10-generic
drwxr-xr-x 2 root root    4096 2007-02-03 03:12 grub
-rw-r--r-- 1 root root 5889346 2007-02-03 03:12 initrd.img-2.6.17-10-generic
-rw-r--r-- 1 root root   94600 2006-10-20 04:49 memtest86+.bin
-rw-r--r-- 1 root root  942801 2006-12-05 13:21 System.map-2.6.17-10-generic
-rw-r--r-- 1 root root 1745711 2006-12-05 13:21 vmlinuz-2.6.17-10-generic
brian@brian-desktop:~$

---

### Post by marmaladejackson on 2007-02-03
Just tried a couple of edits that knight had suggested ((hd0,0) (hd1,0) (hd0,1) (hd2,0)), no luck. Not even sure what the syntax stands for (hd [disk location], [partition])? or if I have to edit any of the other lines as well.  Anything else I should try?

-B

---

### Post by danielph on 2007-02-03
Yeah I think your XP partition is still there, just getting it to boot is the trick. The problem is Windows gets upset if it is not the first operating system to be found on the disks. That is why grub has the entries for map and chainloader. 

Installing both operating systems on the same disk would be simple in terms of grub.

As igknighted mentioned you can edit the grub options of how to boot on the fly. When you reboot the computer highlight windows and press "e", it will let you edit all the options. When you want to try booting press enter to save the line and press "b". You can do this with all the lines and it is a quick way to test that something works. 

I will take another look later if you haven't got anywhere, but I have to go out now. Good Luck


rootnoverify (hd1,0) would be worth a try

Have you looked at [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

or 

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

It might at least get you up and running again.

---

### Post by danielph on 2007-02-03
OK Having looked over your fdisk -l Windows XP is actually the first disk on your system:

/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS

so I am wondering if we need this map command.

Keeping the disk with XP as the first disk why not make it simply and try:

title      Microsoft Windows XP
root       (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by marmaladejackson on 2007-02-03
OK tried removing the "map" commands and setting hd(0,0).  Screen goes blank and system reboots.  If I leave everything else alone and set (hd0,0) I get a "Starting up..." and it just sits there.  Super Grub seems like it would restore things to normal, but is it safe?  Reading the GRUB man now... Any other suggestions?

---

### Post by danielph on 2007-02-03
Well we need to know if your XP partition can actually boot still. There is not really any reason why it shouldn't. As for it being safe, well you have a backup, right :)

I have never used supergrub, but my experience of grub has been it only affects the MBR and doesn't touch your data. If Supergrub trashes your grub and you can't boot at all, you can reinstall grub from the live CD

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by marmaladejackson on 2007-02-03
Of course I don't have a back up!  That would be admitting that I don't know what I'm doing and might screw it up!  Oh well, lets see what I can find.

---

### Post by marmaladejackson on 2007-02-03
Success!  Sort of...

Using superGrub, I was able to boot XP.  But it doesn't seem logical to me.  Choosing the "Boot Windows" option gave me the same "Error 13...".  If I chose "Boot Linux", on the other hand, it dropped me back to the normal GRUB menu.  On a whim, I chose the XP option there and here I am in XP.  So it seems the XP partition works, GRUB just doesn't know where to look for it.  I think I am going to back up some data before I continue my experiments.  Still open to suggestions on how I can accomplish this without  using the SuperGRUB .iso on every start. 

Again thanks to all who are reading this... I am learning a ton.

---

### Post by danielph on 2007-02-03
Well you should be able to use supergrub to reinstall grub on the MBR of XP partition for you and hopefully it will write you a new /boot/grub/menu.1st on the Linux partition. Not sure how you do this with supergrub, but reading about it seems set up for the job.

---

