---
title: "Help!!!!!!Cant log back into windows!!!!!!"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by madHatterCutsTheChatter on 2007-01-19
I recently reinstalled WinXP, only to find that grub was missing. I installed grub using the Live-Cd using 
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
as a guide but now i cant log back onto my working Windows!!!!!!!!!!!!!!!,:confused: :confused: ](*,) 
 it says something like it doesnt recognize the file system 


HELP!!!!!!!](*,) ](*,)

---

### Post by bodhi.zazen on 2007-01-19
Can you post your windows partition and the windows stanza from /boot/grub/menu.lst ?

---

### Post by madHatterCutsTheChatter on 2007-01-19
What command do i use for that?

---

### Post by tonyr1988 on 2007-01-19
What is your partition scheme? (how many partition, which files systems, etc.) Make sure to let us know how many hard drives you have and the partition names for each, if you know them.

I'm assuming you can boot into Ubuntu still. If you can, attach your /boot/grub/menu.lst file to a reply so we can see what you'll need to do.

PS To open the file via command-line, do:

> gedit /boot/grub/menu.lst

---

### Post by Sef on 2007-01-19
For your partions, open the terminal (Applications > Accessories > Terminal):

then type: ```
sudo fdisk -l
```

For the boot menu, use this command:

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by ciscosurfer on 2007-01-19
> **madHatterCutsTheChatter said:**
> I recently reinstalled WinXP, only to find that grub was missing. I installed grub using the Live-Cd using 
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
as a guide but now i cant log back onto my working Windows!!!!!!!!!!!!!!!,:confused: :confused: ](*,) 
 it says something like it doesnt recognize the file system 


HELP!!!!!!!](*,) ](*,)You may find this link helpful >> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by madHatterCutsTheChatter on 2007-01-19
hope this is what you r looking for....



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
# kopt=root=/dev/hda2 ro

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

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
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

### Post by bodhi.zazen on 2007-01-19
That is it :p

Only problem is it looks good, too good :(

can you post the output of;```
sudo fdisk -l
```

That is a small "L"

---

### Post by madHatterCutsTheChatter on 2007-01-19
Hope this is what u wanted.............


Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          64      514048+  82  Linux swap / Solaris
/dev/hda2              65        1045     7879851   83  Linux
/dev/hda3            1046       19929   151685698+   7  HPFS/NTFS

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36483   293049666    7  HPFS/NTFS

---

### Post by logos34 on 2007-01-19
windows is hda3 (ntfs)...hda1 is linux swap which explains the file system error message

Change the windows entry at bottom of menu.lst to this:
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda3
title Microsoft Windows XP Professional
root (hd0,2)
savedefault
makeactive
chainloader +1

---

### Post by bodhi.zazen on 2007-01-19
> **madHatterCutsTheChatter said:**
> Hope this is what u wanted.............

That would be it :p

> **logos34 said:**
> windows is hda3 (ntfs)...hda1 is linux swap which explains the file system error message

Change the windows entry at bottom of menu.lst to this:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda3
title Microsoft Windows XP Professional
root (hd0,2)
savedefault
makeactive
chainloader +1

And logos34 has the solution ;)

---

### Post by madHatterCutsTheChatter on 2007-01-19
yay!!!!!:D  It Works !!!!!!

Thanx every1 4 their help!!! :)

---

