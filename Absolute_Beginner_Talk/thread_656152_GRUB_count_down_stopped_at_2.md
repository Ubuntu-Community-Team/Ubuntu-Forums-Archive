---
title: "GRUB count down stopped at 2"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by guhpraset on 2008-01-02
Just finished installing another gutsy. This one is weird, the grub countdown stopped at 2, so gutsy did not start automatically. I have to press esc and pick the kernel manually.

Help? I want the usual automatic.

Thankyou

---

### Post by kellemes on 2008-01-02
> **guhpraset said:**
> Just finished installing another gutsy. This one is weird, the grub countdown stopped at 2, so gutsy did not start automatically. I have to press esc and pick the kernel manually.

Help? I want the usual automatic.

Thankyou


You better post menu.lst

---

### Post by guhpraset on 2008-01-02
where/what is menu.lst? you want me to paste it here?

---

### Post by forestpixie on 2008-01-02
menu.list is the list you see to boot from - it's in /boot/grub and yes post it

```
cat /boot/grub/menu.lst
```

---

### Post by guhpraset on 2008-01-02
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# kopt=root=UUID=dce09135-1582-40e1-9cca-1024cd59ec81 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=dce09135-1582-40e1-9cca-1024cd59ec81 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=dce09135-1582-40e1-9cca-1024cd59ec81 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by guhpraset on 2008-01-02
i am really sorry, i dont meant to make that four emoticon

---

### Post by kellemes on 2008-01-02
1- Create backup of this file.. you never know.
2- Change "hiddenmenu" to "#hiddenmenu"
3- Change "timeout 3" to "timeout 20" this is the amount of seconds before default OS will boot.

---

### Post by Eddie Wilson on 2008-01-02
Hello,
I really didn't see anything wrong with your menu.lst. The timeout is set to 3 sec. I have mine set on 5 but that should not be a problem. Change your timeout and see what happens. Sorry, I wish I could have helped more
Eddie

kellemes is right. I didn't see the hidden menu item. Thats one on me.(Like its never happened before)

---

### Post by philinux on 2008-01-02
From synaptic install and then run 

startupmanager

It might cure your problem.

The menu item ends up in system>admin

---

### Post by ~LoKe on 2008-01-02
> **kellemes said:**
> 1- Create backup of this file.. you never know.
2- Change "hiddenmenu" to "#hiddenmenu"
3- Change "timeout 3" to "timeout 20" this is the amount of seconds before default OS will boot.

Did you actually mean 20?  That's an excessive amount of time.  And my /boot/grub/menu.lst is the same...
> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

---

### Post by kellemes on 2008-01-02
> **~LoKe said:**
> Did you actually mean 20?  That's an excessive amount of time.  And my /boot/grub/menu.lst is the same...


Well, it's up to you, I have it on 40 actually.. I have tons of kernels in my list so need some time before I decide. :popcorn:

I understood @OP also had an issue with the timeout.

---

### Post by forestpixie on 2008-01-02
i thought op's problem was that it didn't start automatically - gets to 2 and stops

---

### Post by ~LoKe on 2008-01-02
> **forestpixie said:**
> i thought op's problem was that it didn't start automatically - gets to 2 and stops

That's the impression I got as well.

---

### Post by kellemes on 2008-01-02
Indeed you guys are right..
I stand corrected.

---

