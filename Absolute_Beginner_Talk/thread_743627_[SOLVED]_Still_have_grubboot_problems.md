---
title: "[SOLVED] Still have grub/boot problems"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by BoJaNgLes19 on 2008-04-02
if anyone can help me with this my problem has gone unsolved:

2 hdd's

vista on one
ubuntu on the other

went through cd install process, rebooted and it launched straight into vista

upon putting the cd in again, i booted from it, and selected the option: "install from first hard drive" and it gives me a grub boot screen where i can choose my OS.  Other than doing it this way, i CANNOT GET THAT GRUB SCREEN TO LAUNCH.  

I went through the options/possible fixes suggested by others, (thank you to those who tried to help!) but was unable to get any to work.  The last thing i did was backup a copy of my grub in ubuntu, try to boot from it, and failed.  Now that last option on the cd wont work either.  :(

I cant get to my ubuntu OS, and i really want to, so please help!

Here is a copy of the thread from before: [http://ubuntuforums.org/showthread.php?t=741586](http://ubuntuforums.org/showthread.php?t=741586) 

And here is a copy of my ORIGINAL menu.lst/grub from the terminal (I changed the hdd entries around; i made the hd0,0 to hd1,0 and visa versa as we thought it was a boot mapping error):

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

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
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=9411f1b1-2c10-4663-b49d-1605f9c08a31 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# defoptions=quiet splash

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=9411f1b1-2c10-4663-b49d-1605f9c08a31 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=9411f1b1-2c10-4663-b49d-1605f9c08a31 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

---

### Post by Arthur Archnix on 2008-04-02
Sounds like maybe you've installed grub to the MBR of the second hard-drive... try switchign the two around. Unplug the connectinos to the first and second hardrive, and then switch them. If it boots to ubuntu, fixing it should be simple at that point.

---

### Post by garyed on 2008-04-02
If you can get online download supergrub & burn an iso cd it would probably fix your problem.
Boot with a supergrub CD & follow the instuctions.
It saved me a lot of headaches & its always good to have in an emergency.

---

### Post by BoJaNgLes19 on 2008-04-05
well, after all that work it seems all i had to do was go into my bios and change the hdd boot order.  Everything works great now.  thanks to all who helped!

---

