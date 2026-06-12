---
title: "GRUB Problems"
date: 2005-08-18
forum: Absolute Beginner Talk
---

### Post by kook44 on 2005-08-18
Hi-

I have 2 drives - primary master and slave IDE.  WIn XP on the primary, Ubuntu on the slave.  I had GRUB loaded on the slave, and the BIOS set to boot to that disk first.  I had to do some mapping in GRUB to get XP to boot properly.  I decided to reinstall ubuntu on hdb and now everything is screwy.  I think I accidentally installed GRUB on hda.  After rebooting (BIOS still set to boot to second disk), I got GRUB error 15. I went into the BIOS and switched to boot from the master & rebooted.  This time GRUB came up.  Ubunto boots fine, but if I pick XP, I get an error message that quickly flickers and goes back to the GRUB menu.  I can't read it.

How can I get XP to boot in this configuration?
More importantly, can I get my original configuration back (GRUB & ubuntu on hdb, XP & standard win mbr on hda)?

my menu.lst:
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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1


```

---

### Post by kook44 on 2005-08-19
Ok I manually installed grub on hdb, and now I get
Error 11: Unrecognized device string.
When I try to load XP.

stumped...

---

### Post by Miguel on 2005-08-30
Please forgive the late reply. I've had problems caused by partition magic and I'm browsing for grub errors.

Allright, this is a suggestion. First find where is your win XP with a knoppix disk (or any live cd). Then, edit the winXP part at grub's file: /boot/grub/menu.lst. 

As you now know where winXP lives, translate it to grub jargon: 

hda1 -> hd(0,0)
hda2 -> hd(0,1)
hdb3 -> hd(1,2)

Basically, convert the letter to a number, and then substract 1 to both figures (GRUB starts counting at 0).

I hope it helps

PS: ONLY EDIT THE WINXP PART RELATED TO THE PARTITION

---

