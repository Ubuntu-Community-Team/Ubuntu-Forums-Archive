---
title: "i need to make windows my default boot option"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by isniffcorn on 2006-06-09
hey guys the title pretty much says it all. i need to make windows my default boot option.
I've already tried searching up on the net. i came across this on ubuntu's unoffical guide, ubuntu dapper, but it doesn't help much.

i know i have to edit the menu.lst in grub but i'm not exactly sure what to edit in it

    * Find this line 

...
default     0
...

    * Replace with the following line 

default     X_sequence


so if anyone knows how to help me with my current predicament it woudl be much appreciated.

---

### Post by nanotube on 2006-06-09
[QUOTE=isniffcorn]hey guys the title pretty much says it all. i need to make windows my default boot option.
I've already tried searching up on the net. i came across this on ubuntu's unoffical guide, ubuntu dapper, but it doesn't help much.

i know i have to edit the menu.lst in grub but i'm not exactly sure what to edit in it

    * Find this line 

...
default     0
...

    * Replace with the following line 

default     X_sequence


so if anyone knows how to help me with my current predicament it woudl be much appreciated.[/QUOTE]
well, just count off how many different boot options there are, and place the number of the windows one after the default. so, for example, if windows is the 5th boot selection, make the line look like 
default 4
(because counting starts with 0, not with 1).

and of course, to edit the file you have to use sudo (just in case you don't know that already)

---

### Post by aysiu on 2006-06-09
This is my /boot/grub/menu.lst file, and I've bolded the line that needs to be changed: ```
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
**default         0**

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

splashimage (hd0,6)/boot/grub/splash.xpm.gz

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
# kopt=root=/dev/hda7 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda7 ro quiet
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda7 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,6)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
# title           Other operating systems:
# root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

``` Basically, the numbering starts at 0.

So mine defaults to booting *Ubuntu, kernel 2.6.15-23-386*.
If I wanted Windows to be the default, I'd change *default 0* to be *default 3*, as it's the fourth entry down.

Each time you see the word *title* at the beginning of the line, that's an entry (unless there's a # before it at the beginning of the line).

In other words:
0 Ubuntu
1 Recovery mode
2 Memtest
3 Windows

You have to check your own /boot/grub/menu.lst, though, as Windows may not be #3 for you. Count your entries, starting with 0.

---

### Post by isniffcorn on 2006-06-09
wow talk about making it easy to understand.
thanks a lot guys, you really saved the day, this was frustrating me majorly

---

