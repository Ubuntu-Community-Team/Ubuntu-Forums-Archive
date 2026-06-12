---
title: "Grub problem (?) Windows XP unstartable / Cant mount Windows Drive"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by Irish J on 2006-09-21
Okay, so i've upgraded my Grub to the graphical one, now when i try and boot into windows, it doesnt let me.  As in, i hit enter on Windows XP and it just starts the timeout count again.  I can boot into Linux perfectly.

From linux, i cant see any files on /media/Windows anymore.  I tried using System -> Disks and it says "Inaccessible".

I checked /etc/fstab and it is still included there as i'd added it.

HELP!

---

### Post by Irish J on 2006-09-21
OH, i'm using Xubuntu btw.

---

### Post by b_martinez on 2006-09-21
please post your grub config file. in a terminal

sudo mousepad /boot/grub/grub.conf

then copy and paste it. Will try to help out.
Bill

---

### Post by Irish J on 2006-09-21
> **b_martinez said:**
> please post your grub config file. in a terminal

sudo mousepad /boot/grub/grub.conf

then copy and paste it. Will try to help out.
Bill
Grub.conf is an empty file.

---

### Post by bulldog on 2006-09-21
Think he meand /boot/grub/menu.lst :cool:

---

### Post by Irish J on 2006-09-21
> gfxmenu /boot/grub/message.xubu
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
# kopt=root=/dev/hdd1 ro

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

## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.15-27-686
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-686
boot

title		Debian GNU/Linux, kernel 2.6.15-27-686 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/hdd1 ro single
initrd		/boot/initrd.img-2.6.15-27-686
boot

title		Debian GNU/Linux, kernel 2.6.15-26-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Debian GNU/Linux, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdd1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Debian GNU/Linux, kernel memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title		 Microsoft Windows XP Professional
root 		(hd0,0)
savedefault
makeactive
chainloader	 +1


This was working perfectly before i installed gfxgrub.  I used grub-install again, this time when i went to boot windows it gave me GRUB over and over again :D

I dont actually give a flying sideways...ahem...about the Windows partition, it just has my music and documents on it.

Any help much appreciated!

---

### Post by bulldog on 2006-09-21
Did you try to reinstall GRUB with the live cd?

Did you try to mount your windows with the live cd?

Can't imagine your windows is corrupt,but then again.I'm not familiar at what you've done either.

But let's try some stuff to see if we can get it back again.

---

### Post by Irish J on 2006-09-21
> Did you try to reinstall GRUB with the live cd?

I sure didnt, how would i go about doing it?

---

### Post by bulldog on 2006-09-21
Bootup from the live cd

When logged in do

sudo mkdir /mnt/windows

sudo mount -t ntfs /dev/hda? /mnt/windows

And see in the created windows dir if you can access your files.

---

### Post by bulldog on 2006-09-21
You could indeed try to reinstall GRUB first.

Boot into the live cd and do the following,

When you get to the desktop open a terminal and enter,

Code:

sudo grub


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)


Finally exit the grub shell
Code:

quit

---

### Post by Irish J on 2006-09-21
Thanks very much, i will do that.  This is how i installed the graphical grub.

Now, a quesiton;  I'm dual booting windows as you know, and i have two seperate drives.  Windows is on HDA, and Xubuntu on HDD.

When i try > find /boot/grub/stage1, it doesnt find anything.  Should the MBR be on the 2nd hard drive?  Does it matter?

---

### Post by Irish J on 2006-09-21
Re-installing from the LiveCD seemed to work, didnt give any errors, but when i rebooted, i still had the graphical Grub, and selecting windows XP returned a screen full of GRUB GRUB GRUB GRUB etc.

Neither drives could be mounted in Kubuntu.

---

### Post by Irish J on 2006-09-21
Any more ideas anyone?

---

### Post by teimu on 2006-09-21
If any of the above do not help, try remapping the hd's. I dont know if this is necessary for booting all windows drives, but it works for me. I ran into a problems after installing dapper, and had to use the following technique to make it work.

Change the windows entry to

```
title Microsoft Windows XP Professional
map (hd0,0) (hd0,1)
map (hd0,1) (hd0,0)
rootnoverify (hd0,0)
savedefault
chainloader +1
makeactive
boot
```

Notice that
there is a remapping command of partitions for lines 2 and 3
'root' became 'rootnoverify'
makeactive is after the chainloader
boot has been appended

This is the exact method for booting winxp, as the GRUB docs say. Try it. make sure to backup menu.lst first.

Good luck!

---

