---
title: "Can't boot into ubuntu"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by hrolfp on 2007-11-28
Hi,

I'm having trouble booting into Ubuntu. Whenever I try to boot into Ubuntu from GRUB I get the error 'error 15 file not found', but I can boot into my windows partition just fine. I mounted my ubuntu partition  on windows and found that the OS is still there. Not sure what's causing the problem, help would be appreciated.

---

### Post by PeterJS on 2007-11-28
> **hrolfp said:**
> Hi,

I'm having trouble booting into Ubuntu. Whenever I try to boot into Ubuntu from GRUB I get the error 'error 15 file not found', but I can boot into my windows partition just fine. I mounted my ubuntu partition  on windows and found that the OS is still there. Not sure what's causing the problem, help would be appreciated.


Error 15 is the error code for a parsing error in the grub config file. Since you have the ext3 driver installed for windows could you grab your grub configuration and post the section for the kernel you were trying to boot?

---

### Post by hrolfp on 2007-11-28
where would i find it? i'm assuming its in /boot/grub, but there's a bunch of files here and i'm not sure which one it is

---

### Post by PeterJS on 2007-11-28
> **hrolfp said:**
> where would i find it? i'm assuming its in /boot/grub, but there's a bunch of files here and i'm not sure which one it is

Yep, good call. The config file you're looking for is menu.lst.

---

### Post by hrolfp on 2007-11-28
here's the output:

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
# kopt=root=UUID=d3e775c9-e454-4962-a496-5a33d83507f4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d3e775c9-e454-4962-a496-5a33d83507f4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d3e775c9-e454-4962-a496-5a33d83507f4 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by PeterJS on 2007-11-28
> **hrolfp said:**
> 

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=d3e775c9-e454-4962-a496-5a33d83507f4 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet



This is the part that's important to the matter at hand. After a bit more googling, it looks like the documentation I read previously was incorrect, error 15 is file not found. Do you have have:
/boot/vmlinuz-2.6.22-14-generic
and
/boot/initrd.img-2.6.22-14-generic

---

### Post by hrolfp on 2007-11-28
> **PeterJS said:**
> This is the part that's important to the matter at hand. After a bit more googling, it looks like the documentation I read previously was incorrect, error 15 is file not found. Do you have have:
/boot/vmlinuz-2.6.22-14-generic
and
/boot/initrd.img-2.6.22-14-generic

yes, they're both there

---

### Post by PeterJS on 2007-11-28
Well this is a puzzler. Try this, grub has a minimal bash like shell, reboot, and press 'c' to get to the shell. Once there try to use the find command:
```

find /boot/vm

```
This won't work, but from there use tab completion to find the kernel and it will tell you which partition it is on, if this doesn't match the partition set by the root directive that would cause this problem.

---

### Post by hrolfp on 2007-11-28
what command should i type to find the kernel? find  /vmlinuz-2.6.22-14-generic ?

---

### Post by PeterJS on 2007-11-28
```

Find /boot/vm

```
And then use tab completion from there.

The exact command would be:
```

find  /boot/vmlinuz-2.6.22-14-generic

```
But that's a lot to type out, which is why tab completion is nice.

---

### Post by hrolfp on 2007-11-28
the output is (hd0,5)

I think, but I'm not sure, that my ubuntu partion number is 4 not 5. How would I check this?

---

### Post by PeterJS on 2007-11-28
> **hrolfp said:**
> the output is (hd0,5)

I think, but I'm not sure, that my ubuntu partition number is 4 not 5. How would I check this?


You did just check, but there are two different number schemes. Grub calls the first partition 0, while linux calls the first partition 1. So (hd0,5) and sda4 are the same partition.

If you look back at the grub config you posted:
```

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=d3e775c9-e454-4962-a496-5a33d83507f4 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

```Grub is looking on (hd0,6) which isn't the the right place at all. So to get ubuntu to start highlight it's boot entry and press 'e' to edit it, and set root to (hd0,5), and the 'b' to boot. This should get your system booted, however the change won't be permanent, once this system is up and running you will need to edit the configuration file so it has the right settings for future boots.

---

### Post by nynoah on 2007-11-28
Peter, is there anyway you can help me too.  I am having the same problem with my grub.  I have a thread for this here.

[http://ubuntuforums.org/showthread.php?t=624999&highlight=grub]("http://ubuntuforums.org/showthread.php?t=624999&highlight=grub")

---

### Post by hrolfp on 2007-11-28
That got rid of the GRUB error - but now once I get past the grub menu ubuntu doesn't load, all I see is a black screen. This is weird

---

### Post by PeterJS on 2007-11-28
All black or is there a small blinking under score in the upper left corner? And what happens if you give it a while to try and boot and press Alt+Ctrl+F1?

---

### Post by hrolfp on 2007-11-28
The screen is all black

---

### Post by PeterJS on 2007-11-28
Well that is patently bad, hopefully somebody wiser than me will find this thread.

---

### Post by ajmorris on 2007-11-28
Do you have access to a live cd? I suggest a grub re-install. If you can get your hands on any linux live cd, boot into it, and i'll talk you through the grub re-install.

---

