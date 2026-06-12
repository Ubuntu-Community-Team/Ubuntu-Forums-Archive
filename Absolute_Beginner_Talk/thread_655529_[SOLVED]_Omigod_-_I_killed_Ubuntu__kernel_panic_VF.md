---
title: "[SOLVED] Omigod - I killed Ubuntu : kernel panic VFS issue"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by clayts450 on 2008-01-01
Rather foolishly, and ever the tweaker, I decided to implement the recommended change in the fifth post on [this thread]("http://ubuntuforums.org/showthread.php?t=580903"). Regrettably it has trashed my Ubuntu meaning I'm stuck using Windows at present.

After selecting either ubuntu 2.6.22 or ubuntu 2.6.22 (single user mode) I get stuck with the following lines on the boot screen :

Kernel panic - not syncing VFS : Unable to mount root fs on unknown-block (0,0)
VFS cannot open device "UUID-load of numbers and letters" or unknown-block (0,0)

I have tried editing the entries on grub by using ESC and 'e', changing it so that it links directly to the relevant partition (in my case /dev/hda2 - also tried dev/sda2) but the same thing occurs.

I can see all the relevant files using explore2fs if you need specific files etc, but clearly cannot change anything therein

If anyone is willing to help that would be great - there in one big problem, unfortunately, as my Ultrabay has failed on my T22 Thinkpad,so I can't boot from a live CD at the present time (is it possible to boot from a live CD in another computer on my home network ?).

Here's what my menu.lst file contains at present :



[PHP]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=20e2882f-46bd-48a2-9f6d-fbfa3a212ed4 ro

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
# altoptions=(single-user mode) single

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=20e2882f-46bd-48a2-9f6d-fbfa3a212ed4 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (single-user mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=20e2882f-46bd-48a2-9f6d-fbfa3a212ed4 ro single
initrd		/boot/initrd.img-2.6.22-14-generic


title		Ubuntu 7.10, memtest86+
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
title		Windows 98SE
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by blueridgedog on 2008-01-01
So, you think you have tried something like this:

title testsetup
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 
initrd /boot/initrd.img-2.6.22-14-generic

Try the "e" approach and see if you can specify the simple kernel root as above.

---

### Post by blueridgedog on 2008-01-01
Also, what files are in 

/boot

---

### Post by clayts450 on 2008-01-01
Hi blueridgedog - thanks for the response

[Contents of boot folder](http://img184.imageshack.us/img184/8931/contentsofbootxr6.jpg)

[Contents of grub folder](http://img184.imageshack.us/img184/1131/contentsofgrubdm7.jpg)

Yes, I tried :

kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/hda2

as this is where my Ubuntu partition is - I didn't touch the other entries

---

### Post by blueridgedog on 2008-01-02
Can you post a pic with details showing?  The filenames are cut off.

---

### Post by clayts450 on 2008-01-02
Oops - sorry

[Boot folder](http://img156.imageshack.us/img156/749/bootqb2.jpg)

[Grub folder](http://img140.imageshack.us/img140/6629/grubbz8.jpg)

---

### Post by blueridgedog on 2008-01-02
Here are some suggestions, you will need to use the "e" option to try and boot them, if they work, then you can edit menu.lst in /boot/grub.

**First try booting the with the backup initrd image**

kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/hda1
initrd /boot/initrd.img-2.6.22-14-generic.bak

**Alternately, try an older kernel:**

kernel /boot/vmlinuz-2.6.20-16-generic root=/dev/hda1
initrd /boot/initrd.img-2.6.20-16-generic

Remove the quiet splash vga=791and quiet entries.  Also, if these fail, try changing the root specification above.

Remember too when using the "e" option to adjust boot parameters, you need to enter to save and press "b" to boot once you have configured an entry.

I see no reason you should not be able to boot with either of the two options above.

---

### Post by Knoll318 on 2008-01-02
Is your Ubuntu backed up?  If it is, you could always install Wubi on Windows and use LVPM to mount it onto your partition.

---

### Post by clayts450 on 2008-01-02
Right - good news :)

I've managed to boot into the older kernel 2-6-20-16 (I actually had to use /dev/hda2)

Thank you Mr blueridgedog, sir

Couple of queries now

 - what do I do next to get it back to 2-6-22-14
- for some bizarre reason I cannot mount my Windows volume anymore (I need it as I share my Firefox profile with Ubuntu - am using Opera at the moment)

---

### Post by clayts450 on 2008-01-03
fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2745    22049181    c  W95 FAT32 (LBA)
/dev/hda2            2746        4773    16289910   83  Linux
/dev/hda3            4774        4864      730957+   5  Extended
/dev/hda5            4774        4864      730926   82  Linux swap / Solaris

---

### Post by clayts450 on 2008-01-03
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=20e2882f-46bd-48a2-9f6d-fbfa3a212ed4 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=df0c9644-8080-46a8-b2ed-15ea954ebc4c none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0
/dev/sda1    /media/windows vfat  iocharset=utf8,umask=000  0    0

---

### Post by blueridgedog on 2008-01-03
Did you try the new kernel with /dev/hda2?

As to restoring the new kernel, I would try the following (hopefully others who have done this will chime in).

1.  rm /boot/initrd.img-2.6.22-14-generic and cp /boot/initrd.img-2.6.22-14-generic.bak to /boot/initrd.img-2.6.22-14-generic and try rebooting with your normal process

1.  Use apt-get to remove 2.6.22-14, then reinstall

---

### Post by clayts450 on 2008-01-03
Yeah 2.6.22-14 will not boot using /dev/hda2 - straight to the kernel panic message

I've edited menu.lst so that it can go to the safe 2.6.20 kernel (managed to stick in the UUID too) but still have the problem with the inability to mount the Windows partition.

Will try your suggestions out but as you say the key is to remove and reinstall the latest kernel, 2.6.22-14 I think.

Will keep you posted - thanks for your help so far : at least I have a *nearly* functioning Ubuntu anyway, which is a massive improvement over where I was on Monday.

Thank goodness I didn't need the CD drive - my Ultrabay has had it (a bit like this old Thinkpad T22 - really on its way out, more's the pity)

---

### Post by blueridgedog on 2008-01-03
I suspect you have the current sources installed and could compile a new kernel, but it has been so long since I compiled one, I would be hesitant to give you advice.

I suspect that some of your modules are build for the later kernel and that is the root of the errors you have now.

---

### Post by clayts450 on 2008-01-03
I managed to get Windows back by editing the /etc/fstab file

(sudo gedit /etc/fstab in a terminal : save the changes afterwards)

For some reason the reference to the Windows partition had changed from hda1 to sda1

As soon as I corrected it up popped the Windows volume on my desktop :)

So, aside from running a slightly out of date kernel, I'm virtually back to where I was before I started meddling :)

---

### Post by clayts450 on 2008-01-03
blueridgedog - your tip about removing the old /boot/initrd.img-2.6.22-14-generic file and then copying the back-up file in its place worked like a charm.

I then went into my menu.lst file and changed the entry back to the UUID number and it booted perfectly.

For some bizarre reason then my Windows wouldn't mount - but then after doing a sudo fdisk -l I discovered :

```
sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2745    22049181    c  W95 FAT32 (LBA)
/dev/sda2            2746        4773    16289910   83  Linux
/dev/sda3            4774        4864      730957+   5  Extended
/dev/sda5            4774        4864      730926   82  Linux swap / Solaris

```

For some bizarre reason all the hda entries have become sda entries !!!

A quick edit of my fstab file again (from hda1 to sda1) and now Windows mounts too.

I'll need to investigate why it's changed to sda (is that not SCSI ? This is definitely an IDE machine).

In the meantime thanks to your help (and included for future reference below) I was able to solve the problem by :

(1) Pressing ESC when the Grub menu came up, clicking on the first entry (generic)
(2) Pressing 'e' to edit on the line starting 'kernel'
(3) Replacing the text so it reads /dev/hda2 (or wherever your Linux partition is) in place of the UUID number (probably not essential)
(4) Replacing the kernel number 2.6.22-14 with 2.6.20-16
(5) Pressing enter to save
(6) Going down to the line starting initrd and pressing 'e'
(7) Replacing the kernel number 2.6.22-14 with 2.6.20-16
(8) Pressing enter to save
(9) Pressing 'b' to boot
This then takes you to the older kernel, 2.6.20-16, with a fully functioning desktop

Then I did the following (Applications>Accesories>Terminal)

(10) sudo rm /boot/initrd.img-2.6.22-14-generic
(11) sudo cp /boot/initrd.img-2.6.22-14-generic.bak /boot/initrd.img-2.6.22-14-generic
(12) sudo gedit /boot/grub/menu.lst
(13) removed the vga=791 at the end of the line starting 'kernel' directly under the line ##End of Default Options## and saved the file

To fix my mounting problem
(1) Accessories>Applications>Terminal
(2) sudo fdisk -l (<-that's a small L)
(3) Make a note of the windows partition
(4) sudo gedit /etc/fstab
(5) Find the relevant line relating to windows and ensure the Windows partition marries up  with the entry for the windows partition in fdisk -l - if it does not, change it and then save it

Job's a good 'un.

Thanks ever so much for your assistance, blueridgedog - truly, truly appreciated :)

---

### Post by blueridgedog on 2008-01-03
Thanks for the wrap up...perhaps others will benefit.  I try and snag a few unanswered posts a day and sometimes you wade into a tough one.  You are actually a pretty good Linux hacker and didn't need help as much as confirmation that you were working in the right area.

---

