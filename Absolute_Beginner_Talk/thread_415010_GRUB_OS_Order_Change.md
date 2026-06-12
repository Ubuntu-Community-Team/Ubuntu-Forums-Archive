---
title: "GRUB: OS Order Change"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Sethalos on 2007-04-20
Hello.

I'm a very new Ubuntu user (less than a week) and have to say I'm extremely impressed and enjoying the change from Windows. I have been reading alot on the different terminal commands and trying to build my linux knowledge as much as possible. I have been able to install, configure, and run almost every program I require now.

However, I have to dual boot Windows XP (for work) and I'd like it to be the default OS to be loaded when the computer is booting. Currently it is Ubuntu. I'm not sure of the steps to configure GRUB to do this. I have some idea, but I don't want to make a mess of things. If anyone has the steps or advice I'd appreciate it.

Hopefully, I can configure my Windows apps to run through WINE and not have to ever use XP again, but until then, I have to keep Microcraps XP on my system.

Seth

---

### Post by Rinzwind on 2007-04-20
You need to modify the "grub.conf" . The file is located at /etc/grub.conf The file should have a line like this:

**default=0**

Change the number with the one you need (start counting with 0 tho ;) )

gksudo /etc/grub.conf if you use Gnome.
sudo kate /etc/grub.conf if you use KDE.

---

### Post by odin1965 on 2007-04-20
Actually, you need to edit /boot/grub/menu.lst

The rest is correct. Find the line near the top that has "default num" and change num to the number of the OS you want to boot by default. The first entry is 0, then 1 and so on. Uncomment it if it commented.

## default num   <===== original

default 3             <===== new

Then save the file.

---

### Post by Sethalos on 2007-04-20
Thanks Very Much.  I'll try that.

I have to say, that the Linux community is the most helpful I've ever seen.  Kudos to all of you for sharing your knowledge with the Linux noobs.

Seth

---

### Post by odin1965 on 2007-04-20
I just tried my own advice on a new 7.04 install and it still boots Ubuntu every time. The only way I can get it to boot windows is to cut and paste the windows entry in menu.lst from below the automatic Ubuntu entries to just above them. 
  
Weird, I know I've had this working before, but now grub just loads which ever OS is highlighted after the timeout at boot and this is always the top entry.

---

### Post by Robert98374 on 2008-03-16
Ok so i want to do the same thing but i am kinda lost on where i need to change to have XP automaticly load.

heres my grub

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
#      password Edited for post
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
# kopt=root=UUID=8b02e504-5349-46c2-af21-5433168fe10b ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8b02e504-5349-46c2-af21-5433168fe10b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8b02e504-5349-46c2-af21-5433168fe10b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title Microsoft Windows XP Professional
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1

---

