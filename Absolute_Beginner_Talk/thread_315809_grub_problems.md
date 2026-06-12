---
title: "grub problems"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2006-12-09
here is the output of cfdisk:

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    hda1                    Primary   Linux ext3                       41858.45
    hda3        Boot        Primary   Linux ext3       [/]             15759.64
    hda4                    Primary   Linux ext3                       21056.72
    hda5                    Logical   Linux swap / Solaris              1348.95

here is my menu.lst file:

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
hiddenmenu

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
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

title		Slackware 11
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386
initrd		/boot/initrd.img-2.6.15-27-386
boot		

### END DEBIAN AUTOMAGIC KERNELS LIST


```

Im trying to get slackware to boot, this is installed on hda4, can anyone spot the problem?

Thanks tom

---

### Post by bollix47 on 2006-12-09
Try changing (hd0,2) to (hd0,3) using:

gksudo gedit /boot/grub/menu.lst

---

### Post by tommy1987 on 2006-12-09
I seem to get the following error when trying to boot into it:

Filesystem type is ext2fs, partition type 0x83

kernel /boot/vmlinuz-2.6.15-27.386

Error 15: File not found

---

### Post by randiroo76073 on 2006-12-09
If that doesn't work try changing it to (hd0,5)
HTH

---

### Post by igknighted on 2006-12-09
I have found that this:
```
title		      Slackware 11
root		      (hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386
initrd		/boot/initrd.img-2.6.15-27-386
boot	
```
tends not to work well.  I would write this like this:
```
title		Slackware 11
kernel		(hd0,2)/boot/vmlinuz-2.6.15-27-386
initrd		(hd0,2)/boot/initrd.img-2.6.15-27-386
boot	
```

Also, double check your kernel and initrd files.  Those ones look suspiciously like your Ubuntu ones.  Slackware actually defaults to a 2.4 kernel, so unless you changed it yourself those are Ubuntu kernels you are trying to point to.  If this appears to be the case, try this:

Set up you grub entry as I suggested (with the (hd0,2) in front of the lines, even with the wrong kernel listed.  Then restart and try to boot it.  It should send you back to grub with an error.  Now move the cursor over the Slackware entry and hit 'e'.  Then move your cursor over the kernel line and hit 'e' again.  Now you should be able to edit the line.  Delete the path to the kernel down to '(hd0,2)/boot/' then hit tab and it should give you a list of files in that directory.  If it doesn't give you the proper list, try '(hd0,3)/boot/' and hit tab again.  There should be several files, one is a kernel and goes here in this line (should say vmlinuz in the name).  Once you start typing the filename hit tab and it will auto complete.  After this you need a space then root=/dev/hda3 or root=/dev/hda4 (One more than the one in (hd0,x) from before).  Hit enter when the proper file is added and it will take you to the previous screen.

Now move down to the initrd line and hit 'e' again.  Start with the same (hd0,x)/boot/ that you did before, and find an initrd file.  It may say 'initrd-2.4.xx' or maybe 'System...'.

EDIT: I almost forgot, jot down on paper the combo you end up using, because it wont save, so you need to go into ubuntu to edit the menu.lst file with the lines that worked.

---

