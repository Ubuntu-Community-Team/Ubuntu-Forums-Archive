---
title: "Help with setting up Ubuntu for Dual-booting with Windows"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Simon Flavelle on 2007-07-27
Hi all, me again ^^; I've been using Windows again for a while, I would've been using Ubuntu again sooner if it hadn't been for the fact that I want to make absolutely sure that I'll still be able to boot back into XP (I'm a little bit paranoid, I admit :/ ).

I'm currently running off the Live CD of 7.04 for now. Here's the results of **sudo fdisk -l**:

Disk /dev/hda: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1246    10008463+   7  HPFS/NTFS <-- XP Files Drive, This is C:

Disk /dev/hdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       12988   104326078+   7  HPFS/NTFS <--- XP System Partition. G:
/dev/hdc2           12989       24509    92542432+  83  Linux <--- Old Ubuntu Drive. Accessible in Windows through a third-party plugin. U:
/dev/hdc3           24510       24792     2273197+   5  Extended
/dev/hdc5           24510       24792     2273166   82  Linux swap / Solaris

Is there anything else I should post?

---

### Post by tomcheng76 on 2007-07-27
post your /boot/grub/menu.lst

---

### Post by Simon Flavelle on 2007-07-27
> **tomcheng76 said:**
> post your /boot/grub/menu.lst
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
# kopt=root=UUID=b9062058-de7b-4b0f-b7da-0de9a11857a1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b9062058-de7b-4b0f-b7da-0de9a11857a1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b9062058-de7b-4b0f-b7da-0de9a11857a1 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Windows XP Professional
rootnoverify (hd1,0)
savedefault
makeactive
[b]map (hd0) (hd1)
map (hd1) (hd0)[/b] <-- This was from a suggestion from another user when I was having problems booting into XP. I have yet to revert it.
chainloader +1

```

---

### Post by tomcheng76 on 2007-07-27
are you using grub when u choose to boot windows (choose window in the grub menu) ?
i dont notice any problem inside your grub menu file
can u boot to linux ?

---

### Post by Simon Flavelle on 2007-07-27
Windows is currently using the MBR, not GRUB.

There *was* a suggestion by another user to get it working, but is this really temporary?
> **confused57 said:**
> I don't know if it will help, but you can try adding mapping lines to your Window's entry:
```
title Windows XP Professional
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

If you're able to boot first to your hdc drive you could try installing grub to it's mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Using the above link:
```
sudo grub
find /boot/grub/stage1
```
this should return "root (hd1,1)", you would then:
```
root (hd1,1)
setup (hd1)
quit
```

Then booting first to your hdc drive should give you a grub menu...if you get a grub menu at boot, highlight your Ubuntu entry press "e", change root from (hd1,1) to (hd0,1), then press "b" to boot...this change is temporary, but you can see if it will work.  You could also try booting your Windows using this method, by using your original Window's boot entry, but changing root to (hd0,0)...this will let you know if the change will allow you to boot your Window's partition.  As I mentioned, this change is temporary for booting, but it might be worth trying to see if it will work...if it does, then you can make it permanent.  It won't affect your original setup by installing grub to your hdc mbr.

The 3rd link in my signature has some instructions on how to edit your /boot/grub/menu.lst, if the changes work and you want to make it permanent.

---

### Post by tomcheng76 on 2007-07-27
temporary is the procedure here
> you get a grub menu at boot, highlight your Ubuntu entry press "e", change root from (hd1,1) to (hd0,1), then press "b" to boot...this change is temporary
if you do that and successfully boot, you have to make the permanent change by editing menu.lst file yourself
e , e and b changes will not be saved

just try what [this]("http://ubuntuforums.org/showthread.php?t=224351") said

you have large possibility to have a dual boot
if it doesnt work, just try using e , e , b to change the (hd1,1) to (hd0,1)

---

### Post by Simon Flavelle on 2007-07-28
I was able to boot to both drives successfully from using the quoted instructions (although "fkcs" or something failed with Error Code 1). I shall try permanently making the dualboot soon.

---

### Post by Simon Flavelle on 2007-07-28
> **Simon Flavelle said:**
> I was able to boot to both drives successfully from using the quoted instructions (although "fkcs" or something failed with Error Code 1). I shall try permanently making the dualboot soon.

It works! Thanks a lot! :D

---

### Post by tomcheng76 on 2007-07-28
glad to know to establish dual boot :)

---

