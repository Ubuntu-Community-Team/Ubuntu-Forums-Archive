---
title: "Asking for CD to boot"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by akshaya on 2007-08-20
I have window 2000 in one hard drive (primary) and installed Ubuntu 7.04 on a second one one(hd1 slave) in which I had Suse 10.2.

I installed Ubuntu 7.04 from a Ubuntu CD. Did not have any problems.  working fine.  But every time I start, It asks for CD.  It takes me to the installation screen, where I choose "boot it from the first hard drive".  I works fine.

I have set BIOS in all possible combinations, doen't work. 

Help from GURU's please.

Thanks.

---

### Post by Hobo Joe on 2007-08-20
Check your BIOS and make sure that the primary boot device is the harddrive.

---

### Post by akshaya on 2007-08-20
Thanks. 

The primary master is the hard drive with windows.  Primary slave is the hard drive with Ubuntu 7.04. 

Boot sequence that works:
 1 HDD with Ubuntu
2 CD Drive
3 HDD with windows.

Any other suggestions.

Thanks.

---

### Post by expatCM on 2007-08-21
> But every time I start, It asks for CD

What asks for the CD?   You power on and it runs the POST check .....  then what?

---

### Post by AceofSpades19 on 2007-08-21
take the cd out of the drive

---

### Post by TeaSwigger on 2007-08-21
> **akshaya said:**
> I have window 2000 in one hard drive (primary) and installed Ubuntu 7.04 on a second one one(hd1 slave) in which I had Suse 10.2.

I installed Ubuntu 7.04 from a Ubuntu CD. Did not have any problems.  working fine.  But every time I start, It asks for CD.  It takes me to the installation screen, where I choose "boot it from the first hard drive".  I works fine.

I have set BIOS in all possible combinations, doen't work. 

Help from GURU's please.

Thanks.

Hello,

Did you have the ubuntu install replace the Windows bootloader on that drive 1 or is GRUB installed on the second drive..?

Regardless you might want to post your GRUB menu.lst so the folks here can see if there's anything wrong with its configuration first.

---

### Post by akshaya on 2007-08-21
I will try to answer all in this post.

After insalling Ubuntu 7.04, I took the CD out and sarted computer.  
after the usual test it stopped saying

  Boot from CD
  Error loading operating system

I put back the Ubuntu Installation CD  and restarted by pressing ALT+CNTL+DEL

The Ubuntu installation page came up with options:

  



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
timeout		30

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=de07baa4-a8e7-478f-a1c9-21ae86aa1e9d ro

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
# defoptions=splash vga=769 quiet

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=de07baa4-a8e7-478f-a1c9-21ae86aa1e9d ro splash vga=773
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=de07baa4-a8e7-478f-a1c9-21ae86aa1e9d ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=de07baa4-a8e7-478f-a1c9-21ae86aa1e9d ro splash vga=773
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=de07baa4-a8e7-478f-a1c9-21ae86aa1e9d ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
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
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by akshaya on 2007-08-21
I posted before it was complete by mistake.

I will try to answer all in this post.

After insalling Ubuntu 7.04, I took the CD out and sarted computer.
after the usual test it stopped saying

 -Boot from CD
 -Error loading operating system

I put back the Ubuntu Installation CD and restarted by pressing ALT+CNTL+DEL

The Ubuntu installation page came up with options:
  -start installation
 -
 -
 -
 -memory test
 -Boot from first Hard Drive

I chose the the last option.

The page came up with options:
 -Ubuntu kernel26.20-16..
 -
 -
 -windows 2000

Of course I chose the first option.  Ubuntu comes up.

I have pasted the  GRUB menu.lst below.  Please see if there are any problems.  since I am fairly new, I do not understand much.

Thanks for all the help from you guys.


# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 30

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=de07baa4-a8e7-478f-a1c9-21ae86aa1e9d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash vga=769 quiet

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title Ubuntu, kernel 2.6.20-16-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=de07baa4-a8e7-478f-a1c9-21ae86aa1e9d ro splash vga=773
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=de07baa4-a8e7-478f-a1c9-21ae86aa1e9d ro single
initrd /boot/initrd.img-2.6.20-16-generic

title Ubuntu, kernel 2.6.20-15-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=de07baa4-a8e7-478f-a1c9-21ae86aa1e9d ro splash vga=773
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=de07baa4-a8e7-478f-a1c9-21ae86aa1e9d ro single
initrd /boot/initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
root (hd1,0)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows 2000 Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

---

