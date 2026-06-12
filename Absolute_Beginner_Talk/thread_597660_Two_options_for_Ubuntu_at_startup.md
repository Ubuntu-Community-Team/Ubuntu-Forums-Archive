---
title: "Two options for Ubuntu at startup"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by Padraig1 on 2007-10-30
Hi,
I've XP and Ubuntu on this laptop. Recently I reloaded XP and after that when I start the PC I get two options for Ubuntu and one for XP.

It's not causing a problem but I was just scratching my head about why it happened. Any ideas?

oh, and keep the explanations simple if you can. Thanks.

---

### Post by eapache on 2007-10-30
You probably updated the linux kernel (Feisty to Gutsy will do this). The linux kernel is the core of ubuntu and all linux distros. Because it is so low-level, updating it has a high possibility of breaking something, so they leave the old version in as well. If the new version does break something, you can still boot with the old one.

---

### Post by nest on 2007-10-30
post your grub **to be sure**.

but my guess is that the second ubuntu is the old kernel. im pretty sure.

thats because when you update the kernel, shitty things could happend, so you can start perfectly with the older one.

---

### Post by mikewhatever on 2007-10-30
What do you mean by 'reloaded XP'? Reinstlled? Rebooted? Other? Could it be that one option is Ubuntu proper and the other is the recovery mode?

To make things clear, post the output of the following:
> cat /boot/grub/menu.lst

---

### Post by Padraig1 on 2007-10-30
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=4eeec81c-315b-4f43-a74a-3e91fb564884 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=4eeec81c-315b-4f43-a74a-3e91fb564884 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=4eeec81c-315b-4f43-a74a-3e91fb564884 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.20-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=4eeec81c-315b-4f43-a74a-3e91fb564884 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet

title           Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=4eeec81c-315b-4f43-a74a-3e91fb564884 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1





I meant I reinstalled XP.

---

### Post by rudeboyskunk on 2007-10-30
Yeup, you have two kernel versions all right.  You can mark out the ones you don't want to be an option for in grub (mark out means put the # sign in front of the relevant lines), or just leave them in there just in case something screwy happens with the newer kernel version.

EDIT:  Don't worry, this is perfectly normal.  It is what's supposed to happen.

---

### Post by mikewhatever on 2007-10-31
OK, first, reinstalling XP should have nothing to do with adding the second kernel to Ubuntu. I don't know why it says Gutsy next to 2.6.20-16-generic, since that's Feisty's kernel. Have you had Feisty installed and then upgraded?
Anyhow, make sure the newer kernel works fine, use it for a week or two, then remove the older one from synaptic (search for kernel-image and mark the appropriate one for removal).

---

### Post by Padraig1 on 2007-10-31
> **mikewhatever said:**
> Have you had Feisty installed and then upgraded?

Well, I had Feisty installed when I started using Ubuntu a few months ago, and recently I upgraded to Gutsy. I'm not sure if that's what you mean. 

Both kernels are Gutsy when I start them, and if I do something on one it will also appear on the other kernel.

---

