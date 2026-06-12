---
title: "removed windows partition - boot problem?"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by wouterommeslag on 2007-01-20
Hello,

I had a dual boot Windows/ubuntu for some time.

Now I got used to Ubuntu and I could use the Windows disk space. Windows was installed in partition hda1. Now I re-formatted it to ext3; so I could use it in Linux for my music collection.

Question:

I don't dare to reboot my pc. Will I have GRUB problems because I removed my primary partition? If so, what is the solution? 

Help appreciated a lot!

---

### Post by mikewhatever on 2007-01-20
Well, the question is whether formating hda1 wiped the MBR.

---

### Post by JamieC on 2007-01-20
Please attach or post the contents of your menu.lst file (/boot/grub/menu.lst). You may also need to edit fstab (/etc/fstab) to reflect the changes in file system when it comes to mounting.

---

### Post by wouterommeslag on 2007-01-20
I opend the boot.lst:

> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
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
# kopt=root=UUID=3e226830-91dd-418e-9169-17d0961f3443 ro

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

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=3e226830-91dd-418e-9169-17d0961f3443 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=3e226830-91dd-418e-9169-17d0961f3443 ro single
initrd		/boot/initrd.img-2.6.17-10-386
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
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1



---

### Post by je1117 on 2007-01-20
I used to dual boot with Ubuntu and XP. I deleted my ext3 and swap and resized my XP partition to claim the new space. I had to reboot into recover mode and type fixmbr and then do a recovery install - but it's fine now.

---

### Post by JamieC on 2007-01-20
Since you have no operating systems other than Ubuntu, follow the following steps to remove the boot directives for Windows:-

Find:
```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

```

Replace With:
```

# This is a divider, added to separate the menu items below from the Debian
# ones.
# title Other operating systems:
# root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
# title Microsoft Windows XP Professional
# root (hd0,0)
# savedefault
# makeactive
# chainloader +1

```

Are you planning on mounting the new partition?

---

### Post by wouterommeslag on 2007-01-20
The new (ex - windows- partition is mounted with ext3 under /media/music

---

### Post by JamieC on 2007-01-20
Do you plan to mount it by hand on every boot? Otherwise you'll need to add it to fstab.

---

### Post by wouterommeslag on 2007-01-20
I alreadu did ;-) with mount -a I tested it, works just fine :-)

---

### Post by JamieC on 2007-01-20
So you've restarted and everything is fine, yes?

---

### Post by kadeep95 on 2007-01-20
you use "savedefault" two times

---

### Post by wouterommeslag on 2007-01-20
No, i didn't restart yest. I just tested the mount points by remounting all my drives.

But I'm a bit confused: Where is grub on the hard dsik? Was it on my (deleted) windows partition or is it somewhere else (not effected by the delete-operation)?

Question is: is my MBR gone by deleting my hda1 partition?

---

### Post by wouterommeslag on 2007-01-21
Rebooted, everything is just fine, thnank you all!

---

