---
title: "Windows boot problem"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by abuntoyoutoo on 2007-02-07
hey I've recently installed ubuntu and windows xp to my computer. I put xp first then ubuntu. However now I can't get into xp. 

When I start my computer, a list of options appear. It has three ubuntu choices (which work perfectly). Then, under "Other Operating Systems", Windows XP is listed.

When I select Windows XP from that list I get a blue screen with the error:
```

a problem has been detected and windows has been shut down to prevent damage to your computer.

If this is the first time you've seen this stop error screen, restart your computer. If this screen appears again, follow these steps:

Check for viruses on your computer. Remove any newly installed hard drives or hard drive controllers. Check your hard drive to make sure it is properlyconfigured and terminated. Rn CHKDSK /F to check for hard drive corruption, and then restart your computer.

technical information:

*** STOP: (heaps of number which i'm too lazy to type :))

```


Does anyone know how to fix this?

Also, I have ntfs-3g working with read/write for that drive. However, I have to do a force mount to get it to work.

This is the contents of the windows boot.ini file:
```

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

```
Also, my partitions are set up like this
```

WINDOWS (60GB) ----- UBUNTU (68GB) ---- SWAP (4GB)

```

---

### Post by Quintin Riis on 2007-02-07
This is a problem with windows, not Ubuntu.

What is the STOP code?

---

### Post by abuntoyoutoo on 2007-02-07
STOP Code:

STOP: 0x0000007B (0xF795C640, 0xC000000E, 0x00000000, 0x00000000)

---

### Post by Quintin Riis on 2007-02-07
Run chkdsk on the windows partition.

---

### Post by abuntoyoutoo on 2007-02-07
> **Quintin Riis said:**
> Run chkdsk on the windows partition.
How do I do that? Terminal doesn't recognize chkdsk, and I can't get into windows to do it from there.

---

### Post by .Michael on 2007-02-07
Mr. Bill's operating system emo'd out from being out numbered. Thats all

---

### Post by logos34 on 2007-02-07
Do you have a Windows CD?  You can boot from that and go into the recovbery console to run chkdsk from there.  Or download the SystemRescueCd or Gparted LiveCD, open up gparted screen, right-click on the windows partition and select 'Check' and apply.  I think it scans/repairs bad sectors and corrupted files like chkdsk.

---

### Post by rthmchgs on 2007-02-07
abuntoyoutoo, I had the same problem.  Tried installing Ubuntu this past weekend on the same drive as Windows XP.  I think I did it about 6 times, always the same result.  Windows installed and booted fine, Ubuntu installed and booted fine, but then when I went to boot windows and I got the same STOP error.  My friend who is helping me with the install tried it on his machine the exact same way....no problems.   This was with 6.10 and XP.  Sorry to say I don't have a solution.  I ended up installing Windows on C and Ubuntu on D.  I couldn't stand it not working.  I'll post if I find anythign out.  Just wanted to let you know you aren't the only one with this installation problem.

---

### Post by abuntoyoutoo on 2007-02-07
I used my windows xp cd to perform a chkdsk and it reported that the disk had unrecoverable errors on it.

---

### Post by rccharles on 2007-02-08
> **abuntoyoutoo said:**
> hey I've recently installed ubuntu and windows xp to my computer. I put xp first then ubuntu. However now I can't get into xp. 

When I start my computer, a list of options appear. It has three ubuntu choices (which work perfectly). Then, under "Other Operating Systems", Windows XP is listed.



This could be a problem with you grub menu list.  The file is:
/boot/grub/menu.lst

In Ubuntu, you can see the file by:
applications > accessories > terminal

cat /boot/grub/menu.lst

Would it be possible to cut and past here?

While you are at it, could you copy the result of fdisk -l here.

sudo fdisk -l

enter your logon password.

This will create a file:
sudo fdisk -l >seefdisk

...........

Isn't there a windows mbr recovery program?  You could run it.  This would give you access to Windows while taking away Ubuntu.

...........

And superGrub would let you have access to Ubuntu until you got things working.

Another option, would be to use superGrub. This has grub on a bootable CD. In a series of menus, superGrub lets you boot any partition.

Main page:
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

download page:
[http://forjamari.linex.org/frs/?group_id=61](http://forjamari.linex.org/frs/?group_id=61)

superGrub can be a little cryptic, but looking at the screenshot page helps.

[http://supergrub.forjamari.linex.org...on=screenshots](http://supergrub.forjamari.linex.org...on=screenshots)

You cursor down to the line you want.

The help line is
| ================> Windows <=============== |

You cursor down below this line and press enter.

I wrote superGrub out to cd and it worked for me. You can boot your partition even without grub on the partition.


Robert

---

### Post by abuntoyoutoo on 2007-02-08
This will be a fairly long reply, so bear with it :)

Contents of /boot/grub/menu.lst:
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
# kopt=root=UUID=09fafc89-ef34-4990-8d14-2df976d9a1ee ro
# kopt_2_6=root=/dev/hda3 ro

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```


Result of sudo fdisk -l
```

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9561    76798701    7  HPFS/NTFS
/dev/hda2           19378       19929     4433940   82  Linux swap / Solaris
/dev/hda3            9562       19377    78847020   83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9733    78180291    7  HPFS/NTFS

```
> 
Isn't there a windows mbr recovery program? You could run it. This would give you access to Windows while taking away Ubuntu.
But I don't want to lose Ubuntu :) Or did you mean that ubuntu disappears from the menu, but still remains on the machine?

> Another option, would be to use superGrub. This has grub on a bootable CD. In a series of menus, superGrub lets you boot any partition.
This looks promising. Thanks for the link!

---

### Post by logos34 on 2007-02-08
> But I don't want to lose Ubuntu  Or did you mean that ubuntu disappears from the menu, but still remains on the machine?

It just restores ntldr to the mbr--it doesn't affect your ubuntu partitions except that you can't boot into them by default.

Which brings to my suggestion: if you can't get grub/supergrub to boot windows you might try things the other way around--namely, use windows bootloader to boot linux.  Haven't tried it myself, but there is apparently a way to do it by modifying your windows boot.ini file.  Worth a try. You need to restore windows bootloader first.

Start with these links
[http://ubuntuforums.org/showthread.php?t=56723&highlight=boot.ini](http://ubuntuforums.org/showthread.php?t=56723&highlight=boot.ini)
[http://ubuntuforums.org/showthread.php?t=342663&highlight=using+ntldr+to+boot](http://ubuntuforums.org/showthread.php?t=342663&highlight=using+ntldr+to+boot)

But if as you say chkdsk returned unrecoverable errors on it, then that might be a problem.  This might mean there are probably bad sectors on it which could not be repaired.  Did you do a full (as opposed to quick) format of the target partition before installing windows on it?  This is recommended, and if you didn't you might consider reinstalling.    

Also, can you even mount windows partition in linux?

---

### Post by rthmchgs on 2007-02-08
abuntoyoutoo, I forgot to mention that I tried booting the XP cd and using the recovery console.  I used FIXMBR and FIXBOOT, both did not fix the problem.  My friend directed me though editing the grub file, but also no fix.  I would like to know what the problem is.  Sorry, still no ideas though.

---

### Post by torgrot on 2007-02-08
I would be very leary of using ntfs-3g to write to a ntfs partition.  I tried that once inadvertently and had to restore from a backup, which entailed formatting that partition.  I could not boot Windows, nor did FIXMBR and/or FIXBOOT repair the problem.  And yes CHKDSK reported unrecoverable errors on that drive.  It was much easier to get another drive and install Ubuntu to it and Windows to the other.

---

