---
title: "no boot from SATA HD"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by torellig on 2008-01-28
'cause I've got no answer in our italian forum, I try here.

After using livecd for some weeks I have installed ubuntu on a new SATA hard disk Seagate. 
But at the boot it freezes, so no boot.
If I use Livecd all is ok, but if I boot from hard disk, no boot

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c70b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29644   238115398+  83  Linux
/dev/sda2           29645       30401     6080602+   5  Extended
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

on the BIOS the first option is hard disk, and SATA is the only disk, 'cause I have disconneted the other disk, IDE with xp......

what i can do?

---

### Post by phidia on 2008-01-28
It freezes with no error output?

When you boot from the live cd can you navigate to your hard disc install and look at /var/log/messages? There maybe some information there. 

I would also check or try to reinstall grub (check /boot/grub/menu.lst)

hope that helps.

---

### Post by torellig on 2008-01-28
Thanks, Phidia

I try to boot again from HD. Nothing.
 No error message.. nothing
After the first page of boot, all is blank; only a " - " is blinking on the left, up corner..

no bip, nothing..

I have looked at /var/log/messages; I have found on Filesystem/var/log/messages a long log, but I think it is something about the Livecd...

about grub, I have looked at /boot/grub/menu.lst. 
It looks ok.

How can I reinstall grub?

But I'm not sure that the problem is grub..
The Pc freezes too early in the booting.. 

may be something in the bios? but, what??

---

### Post by drowner on 2008-01-28
When you installed Ubuntu did you have the disk with XP attached? It may be possible that the GRUB has been installed to the XP disk - and now that it is disconnected it cannot boot because there is no boot information on the Ubuntu disk.

Show us what grub says (the output of *cat /boot/grub/menu.lst* ) - also try and boot with the windows IDE HD in.

In bocca al lupo!

---

### Post by torellig on 2008-01-29
thank you, Drowner, and excuse me for the delay, but I've finished now my work.

this is: /boot/grub/menu.lst 

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=123cc579-6d61-4348-b8ab-02f27db14817 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=123cc579-6d61-4348-b8ab-02f27db14817 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=123cc579-6d61-4348-b8ab-02f27db14817 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

********************************************Y

Yes I've installed Ubuntu on a absolutely new HD SATA, while the other IDE disk (with Vista) was attached.
The only thing I can tell is that with LiveCd the pc is doing a normal boot, but when I try to boot from HD SATA Seagate with Ubuntu the boot stops immediately after the first prompt..

Is it better to reinstall Ubuntu with attached only the SATA disk? In this case, it is better 7.10 Gutsy Gibbon or the alternate release?
 
If I reinstall, do I have to format? or can I overwrite the installed release?

---

### Post by mahehellraiser on 2008-01-29
Even i had problem booting vista and ubuntu ......but mine was on same HD(SATA) .......and i never solved it...try SUPER GRUB

---

### Post by dstew on 2008-01-29
I think Drowner is right. Your /boot/grub/menu.lst has the grub root partition as (hd1,0), but you do not have an hd1 disk according to your fdisk output. If grub is installed on your remaining disk, it cannot find its root because it is looking for (hd1). You should re-install grub. Boot a live Cd, open a terminal window, and enter **grub**. You will get the grub command line, with the **grub>** prompt. At the grub> prompt enter these commands:```
root (hd0,0)
setup (hd0)
quit
```Then reboot. I am assuming the SATA drive is the only one in your computer.

---

### Post by phidia on 2008-01-29
> **torellig said:**
> thank you, Drowner, and excuse me for the delay, but I've finished now my work.

this is: /boot/grub/menu.lst 

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=123cc579-6d61-4348-b8ab-02f27db14817 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=123cc579-6d61-4348-b8ab-02f27db14817 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=123cc579-6d61-4348-b8ab-02f27db14817 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

********************************************Y

Yes I've installed Ubuntu on a absolutely new HD SATA, while the other IDE disk (with Vista) was attached.
The only thing I can tell is that with LiveCd the pc is doing a normal boot, but when I try to boot from HD SATA Seagate with Ubuntu the boot stops immediately after the first prompt..

Is it better to reinstall Ubuntu with attached only the SATA disk? In this case, it is better 7.10 Gutsy Gibbon or the alternate release?
 
If I reinstall, do I have to format? or can I overwrite the installed release?

You don't need to do a reinstall, at least not yet. Are you wanting to dual boot with windows & linux?
The [community docs]("https://help.ubuntu.com/community/Installation") give good step by step info on that [this]("https://wiki.ubuntu.com/Booting")booting guide is helpful too.

For your specific problem I would just edit menu.lst to reflect the partition being (hd0,0). When you installed with the other drive attached grub saw that partition as hd1,0
If you change that in your menu.lst and save it you should then be able to boot into Ubuntu.

---

### Post by torellig on 2008-01-29
I have done what Dstew told me.
I got this:

grub> root (hd0,0)

Error 21: Selected disk does not exist

grub> setup (hd0)

Error 12: Invalid device requested

grub> root (hd0,0)

Error 21: Selected disk does not exist

grub> setup (hd0)

Error 12: Invalid device requested

grub> quit


Remember that now I have only one HD attached, the Seagate SATA with Ubuntu..

---

### Post by torellig on 2008-01-29
to Phidia

no, I hate Vista
I want to boot with Ubuntu with this PC...

I want to have a second small IDE disk just for those programs that don't run with Ubuntu.

But it is a difficult fight...for me, at least..

---

### Post by drowner on 2008-01-29
Torellig - change your GRUB settings to what they were previously,  and reboot again WITH the vista IDE in there. That will work.

---

### Post by torellig on 2008-01-30
I've used supergrub; it fixed the problem, 'cause there was no grub on sata drive.

Now all it is OK.
So I've attached also the second HD, with Vista

I want to thank all of you for your help

---

