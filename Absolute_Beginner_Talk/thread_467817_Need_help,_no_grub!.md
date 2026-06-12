---
title: "Need help, no grub!"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-06-08
Hi, I installed Ubuntu 7.04 for a friend. And i put Banshee, Avant Window Navigator and Beryl o n it. Then i changed the boot options so that XP boots first. 

But now when i try's to start the comp there is no grub loading stage 1.5 and only the windows xp boot screen is showing, then the computer restartrs and this happens over and over agein.......

Yesterday everything where fine, XP booted first and we got Grub stage 1.5 (yes after i changed the boot options), So now the computer has no working OS, and i'm now sitting on a Ubuntu Live CD, anny help?
Thanks for all answers

Here is my (his) partitions
[[img]http://bildr.no/thumb/73666.jpeg[/img]](http://bildr.no/view/73666)

---

### Post by alienexplorers on 2007-06-08
Try this.  Boot off livecd and enter in terminal:

> sudo grub
next enter in the grub program these lines:

> find /boot/grub/stage1
root (hd0,3)
setup (hd0)

---

### Post by ajmannen on 2007-06-08
[[img]http://bildr.no/thumb/73668.jpeg[/img]](http://bildr.no/view/73668)

Umm.... (sorry if i'm being stupid)

---

### Post by alienexplorers on 2007-06-08
Try this. Boot off livecd and enter in terminal:

:
> sudo grub
next enter in the grub program these lines:


> find /boot/grub/stage1
root (hd0,3)
setup (hd0) 

---

### Post by ajmannen on 2007-06-08
Now Ubuntu wokrs :D

But Windows won't work, i get the same problem when i try to boot windows

---

### Post by flowingfire on 2007-06-08
I've been having nasty grub issues lately myself.  And while I can't really help you, I want to encourage you to fight the good fight and win this battle!  

Taking a look at /boot/grub.lst might help too.  If you edit it as root, you might be able to configure it easily enough if you look at the given examples... Just make sure to leave the Debian comments alone, as I so painfully learned.

---

### Post by alienexplorers on 2007-06-08
enter in terminal
> cat /boot/grub/menu.lst
> cat /boot/grub/device.map
and print results here.

---

### Post by ajmannen on 2007-06-08
> newton@newton-desktop:~$ cat /boot/grub/menu.lst 
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
# kopt=root=UUID=cc9d2cb2-d72c-4a97-9ee1-3e838814e58c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1


title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=cc9d2cb2-d72c-4a97-9ee1-3e838814e58c ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1



newton@newton-desktop:~$ 


Hope that helps

---

### Post by alienexplorers on 2007-06-08
Oops.

---

### Post by alienexplorers on 2007-06-08
## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by ajmannen on 2007-06-08
How do i change that?

---

### Post by ajmannen on 2007-06-08
I mean how can i acces and change the grub list

---

### Post by shifty_powers on 2007-06-08
sudo gedit /boot/grub/menu.lst

type that into a terminal :D

---

### Post by Big_Croc7 on 2007-06-08
I don't think it's a grub/Ubuntu error; if the windows logo comes up, grub has started to load windows, so the problem's with windows rather than grub.  You could maybe try booting from the windows disk and running fixboot.

---

### Post by ajmannen on 2007-06-08
Now either Ubuntu or windows works, when trying to start ubuntu i get error messege 15 and  when trying to start windows i get windows update.

[[img]http://bildr.no/thumb/73695.jpeg[/img]](http://bildr.no/view/73695)

---

### Post by shifty_powers on 2007-06-08
What have you actually done? Edited the menu.lst? Or using fixboot from the windows disk?

Try using **_[this](http://supergrub.forjamari.linex.org/?section=home)_** with **_[this](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#mistake_when_I_edited_my_menu.lst)_** to give you some guidance on it.

---

### Post by alienexplorers on 2007-06-08
In your [COLOR="Red"]menu.lst[/COLOR] you seem to have two files listed for windows.  There should be only one listed unless you are running two different windows distro's.

---

### Post by alienexplorers on 2007-06-08
newton@newton-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=cc9d2cb2-d72c-4a97-9ee1-3e838814e58c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

[COLOR="Red"]## ## End Default Options ##
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Microsoft Windows XP Home Edition
root (hd0,1)
savedefault
makeactive
chainloader +1[/COLOR]


title Ubuntu, kernel 2.6.20-16-generic
root (hd0,3)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=cc9d2cb2-d72c-4a97-9ee1-3e838814e58c ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


[COLOR="Red"]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP
root (hd0,0)
savedefault
makeactive
chainloader +1[/COLOR]

One of the highlighted windows sections is wrong.  Not sure which, but one has to go.

---

### Post by alienexplorers on 2007-06-08
You should also have a 

> /boot/grub/device.map

file with your drive listed.  It should look like:

> cat /boot/grub/device.map
(hd0)   /dev/sda


---

