---
title: "Dual Booting WIndows XP MCE 2005 problem"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by ormeskirk on 2007-05-11
I installed windows XP MCE 2005 on a 500gb SATA drive and Linux on a 250gb PATA drive.  Windows has a 1/2GB partition on that drive because it wanted some space on the first drive to install some boot up stuff.

The problem happens when I try to load windows from Grub.  When I choose it I get a black screen except on the very top left corner it says "Starting Up..." and a cursor is flashing a few lines below.  I cannot type anything or do anything except a hard reboot.  I've let it set for 30 minutes or so and nothing happens.  The only way I can boot into windows is if I boot of the windows disk and repair the MBR, but then I no longer have Grub and cannot boot linux.

Anybody have any thoughts?

Thanks.

---

### Post by Terl on 2007-05-11
Is the drive windows is on the "main drive" of the pc?  Windows is very finicky if it is not "first".

Can you post your grub information (menu.lst )

---

### Post by ormeskirk on 2007-05-11
I've done it both ways.  Windows currently is not on the main drive, but I had the same problem with WIndows on the main drive and LInux on the second drive, and with both on the first drive.

Here's the menu.lst:


title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=37c953d9-72d2-44b9-9db9-b7e99bb0c7ef ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=37c953d9-72d2-44b9-9db9-b7e99bb0c7ef ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by ormeskirk on 2007-05-11
Sorry, here's the first half of the menu.lst

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
# kopt=root=UUID=37c953d9-72d2-44b9-9db9-b7e99bb0c7ef ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

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

---

### Post by Terl on 2007-05-11
Can you post the output of:

```
fdisk -l
``` That is -(small L)

---

### Post by ormeskirk on 2007-05-11
I typed it in a terminal and pressed enter, but there was no output.  

ormeskirk@midnight-leapin:~$ fdisk -l
ormeskirk@midnight-leapin:~$

---

### Post by Terl on 2007-05-11
I apologize.  I should have said:

```
sudo fdisk -l
```

Teach me to work and forum surf :)

---

### Post by ormeskirk on 2007-05-11
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3916    31455238+   7  HPFS/NTFS
/dev/sda2            3917       60800   456920730    f  W95 Ext'd (LBA)
/dev/sda5            3917       60800   456920698+   7  HPFS/NTFS

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          65      522081    7  HPFS/NTFS
/dev/hda2              66       30026   240661732+  83  Linux
/dev/hda3           30027       30401     3012187+   5  Extended
/dev/hda5           30027       30401     3012156   82  Linux swap / Solaris

---

### Post by Terl on 2007-05-11
Well, I am a bit stumped as to how to help.  

Here is what it looks like to me.  Each of your drives thinks it is HD0.  The grub menu.lst shows linux and windows both on hd0 with windows on the hd0,0 sector and Linux starting at hd0,1.  I think the problem is coming from the mix of drive types, one is sata and the other is pata.

As an example, I have two sata drives so one of them is hd0 to grub and the second is hd1 (the fdisk calls them sda and sdb).  With your setup you have an hda (pata disk) and an sda (sata).  Grub has these each as hd0.  I think this is why you cannot boot.  

I will try and google a little... maybe someone else will pop on and help.  There is a workaround I would think, I am just not certain of the fix right now.

---

### Post by ormeskirk on 2007-05-11
Well, WIndows wanted to install it's boot stuff on a small partition on the PATA drive.  So I created a 512mb partition there and it was happy.  It wouldn't install on my SATA drive otherwise.  I think that is why Grub is pointion to that partition.

---

### Post by Terl on 2007-05-11
I did find this link:  [SATA and PATA mix]("http://www.mepislovers.org/forums/showthread.php?t=6754") This is a similar issue (different distribution of linux but it is still debian based) and their solutions might help.

---

### Post by ormeskirk on 2007-05-11
I've tried it with WIndows on my Pata drive and Linux on the Sata drive, but it did the same thing.

---

### Post by ormeskirk on 2007-05-11
Thanks for your help.  I guess the boot loaders don't like the combo of PATA and SATA.

I may try disconnecting one of my drives and see what happens.

Thanks again.

---

### Post by Terl on 2007-05-11
Because of the mixed nature of the drives, Grub is getting confused.  You may have to put windows on your main drive and put grup on the root portion of your linux install.  Check the idea here: [Using windows ntldr to start Linux]("http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why").  It is a Gentoo wiki but it will guide you.  This is the same fix that was discussed in the other link I gave in the prior post.

Do you have a way to make both pata or both sata?

---

### Post by Terl on 2007-05-11
> **ormeskirk said:**
> Thanks for your help.  I guess the boot loaders don't like the combo of PATA and SATA.

I may try disconnecting one of my drives and see what happens.

Thanks again.

Here is another idea.  Maybe use the large drive for both operation systems.  With windows on it first, then install Ubuntu.  Let ubuntu write Grub to the mbr.  Format the second drive as FAT32 and use it as storage for both Linux and windows.

---

### Post by ormeskirk on 2007-05-11
Thanks, you giving me a lot to try.

---

