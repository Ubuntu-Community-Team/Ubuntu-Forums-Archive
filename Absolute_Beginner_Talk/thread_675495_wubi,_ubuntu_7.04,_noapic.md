---
title: "wubi, ubuntu 7.04, noapic"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by mini-milk on 2008-01-22
Hello all, I've searched as much as I can on this problem, and from a complete Ubuntu virgin I think i've got a tiny grasp on whats going on here, but I really need some help!
 
I have used wubi to download ubuntu, and on restart of my pc, I get the timer cannot apic something or another.
 
I think I fixed this by adding 'noapic nolapic noapci noirqpoll nosmp' to my hearts content in the menu.lst file.
 
I think the original menu.lst file looked something like this:
 
```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=find=/wubi/boot/linux ro
 
## default grub root device
## e.g. groot=(hd0,0)
# groot=find --set-root --ignore-floppies /wubi/boot/linux
 
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
 
title Ubuntu
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux quiet splash ro
initrd /wubi/boot/initrd
boot
 
title Ubuntu (Original Kernel)
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=ubuntu-7.04-alternate-i386.iso  ro
initrd /wubi/boot/initrd
boot

```
 
but I've butchered it to something more along the lines of:
 
```

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=find=/wubi/boot/linux quiet splash noapic nolapic noapci noirqpoll nosmp ro
 
## default grub root device
## e.g. groot=(hd0,0)
# groot=find --set-root --ignore-floppies /wubi/boot/linux quiet splash noapic nolapic noapci noirqpoll nosmp
 
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash noapic nolapic noapci noirqpoll nosmp
 
title Ubuntu
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux quiet splash noapic nolapic noapci noirqpoll nosmp ro
initrd /wubi/boot/initrd
boot
 
title Ubuntu (Original Kernel)
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=ubuntu-7.04-alternate-i386.iso quiet splash noapic nolapic noapci noirqpoll nosmp ro
initrd /wubi/boot/initrd
boot

```
 
(I've omitted all the text that I think isn't relevent, but i'll post a full copy of my menu.lst at the end of this post).

Anyway back to the point, I've mashed some commands I know nothing about into a file I know nothing about, and it seems to work, the grub boot loader seems to work, and I get the Ubuntu logo come up and the orange bar underneath start to move, but at a very short distance it seems to freeze, and won't move at all.

So I was wondering, does any one know what im doing wrong/how to help me?

(wubi has downloaded ubuntu, but I have yet to install ubuntu I do believe, as the original noapic error came about at the first restart after the wubi program had finished doing its thing.)

AMD64 x2 processor
nforce4 chipset motherboard

Oh, and I think it might be worth noting that I have found the noapic thingy in my bios, but its stuck on 'enabled', as in its greyed out and cannot be turned to disabled (I had read somewhere on these forums, that disabling noapic in the bios had helped some people).

my menu.lst in D:\wubi\boot\grub as is:

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
timeout		1

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
# kopt=find=/wubi/boot/linux quiet splash noapic nolapic noapci noirqpoll nosmp ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=find --set-root --ignore-floppies /wubi/boot/linux quiet splash noapic nolapic noapci noirqpoll nosmp

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
# defoptions=quiet splash noapic nolapic noapci noirqpoll nosmp

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

title Ubuntu
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux quiet splash noapic nolapic noapci noirqpoll nosmp ro
initrd /wubi/boot/initrd
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title Ubuntu (Original Kernel)
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=ubuntu-7.04-alternate-i386.iso quiet splash noapic nolapic noapci noirqpoll nosmp ro
initrd /wubi/boot/initrd
boot

```

---

### Post by obscur156 on 2008-01-23
I would not recommend using wubi but thats just me.

If you want to install ubuntu,just do a clean install for your dual boot.
i have used a simple tutorial for my dual boot and triple boot without any problem even if i was a total noob to ubuntu.

Follow that link and you will not regret it:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty]("http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty")

Download the ubuntu image you want ,burn it to a cd.
if you already have  windows installed then go straitgh to ubuntu installation following the tutorial.

You will run your ubuntu distro in 25 minutes or less,that is faster then M$.

Good luck and give feed back if you manage to do it.
Best regards,have a nice day.

---

### Post by exneo002 on 2008-01-24
he's right wubi screwed me twice now I'm planning a mint install buy a pack of dvds and back up your data

---

