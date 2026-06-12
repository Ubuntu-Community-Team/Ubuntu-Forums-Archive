---
title: "Missing Spash Screen?"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by kool_kat_os on 2007-12-14
I just upgraded from 7.10 from 7.04 with a clean install and on 7.10 the Boot up and shut down spash screen is missing, whats wrong? (this problem happened on 2 of my computers.

---

### Post by Existentialist on 2007-12-14
I had the same thing happen on a couple computers.  Both were running nvidia gpus so I think it may be something to do with when the driver loads during the boot process.

---

### Post by diatribe on 2007-12-14
check to see that quiet and spalsh are enabled in menu.lst

---

### Post by APMT19 on 2007-12-14
srry for editing this, i changed the name of my usename and I signed on to the wrong one

---

### Post by kool_kat_os on 2007-12-14
Here is the specs of one of my computers, dont know if it helps:

Intel Pentium M processor 1.86GHz
1022MB RAM
160GB Harddrive
ATI MOBILITY RADEON X700
Video Memory: 256.0 MB
1440 x 900 (32 bit) (60Hz)

---

### Post by diatribe on 2007-12-14
maybe you should try following the advice already given?

---

### Post by kool_kat_os on 2007-12-14
Ok

---

### Post by JillSwift on 2007-12-14
Which splash do you mean? The bar-graph splash as you boot (if so, diatribe has given spot-on advice) or the Gnome splash after you log in?

I think the Gnome splash is disabled now by default in Gutsy. You can easily turn it back on with System --> Preferences --> Splash screen. You can even make or download custom splashes easily with that tool.

---

### Post by kool_kat_os on 2007-12-14
I'm talking about the one when you boot up and shut down.  because all I see is a black screen for a minute and I dont know whats goin on, then the login screen eventually appears.

---

### Post by JillSwift on 2007-12-14
> **kool_kat_os said:**
> I'm talking about the one when you boot up and shut down.  because all I see is a black screen for a minute and I dont know whats goin on, then the login screen eventually appears.Ok. So, do this to have a look at menu.lst (please post what it says)

in a terminal, type:```
cat /boot/grub/menu.lst
```
This will show you the contents of the file GRUB uses as its configuration.

---

### Post by kool_kat_os on 2007-12-14
Ok, i'll try that tomorrow, Thanks

---

### Post by diatribe on 2007-12-14
heh

---

### Post by JillSwift on 2007-12-14
> **kool_kat_os said:**
> Ok, i'll try that tomorrow, Thanks
*bangs head on desk*

---

### Post by diatribe on 2007-12-14
> **JillSwift said:**
> *bangs head on desk*

welcome to my world ;)

---

### Post by kool_kat_os on 2007-12-14
ha ha ha :D

---

### Post by kool_kat_os on 2007-12-15
Here is what the 
```
cat /boot/grub/menu.lst
```
came up with: 

[HTML]# menu.lst - See: grub(8), info grub, update-grub(8)
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
default         5

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
# kopt=root=UUID=f37035ca-4e6a-4ec2-88d7-e9afd695491b ro

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
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=f37035ca-4e6a-4ec2-88d7-e9afd695491b ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=f37035ca-4e6a-4ec2-88d7-e9afd695491b ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows XP Media Center Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1
[/HTML]

---

### Post by kool_kat_os on 2007-12-20
Help Me!!!!

---

### Post by Stunt Double on 2007-12-20
My solution from a previous post:     
    I 'm running 7.10 and had the same problem. The solution was to use Synaptic Package Manager to install startupmanager. It's put in System-->Administration-->Start Up Manager. Under the BOOT OPTIONS tab, I changed the Color Depth from 8 bits to 16 bits. That's all it took. Now I have a splash screen when it starts and stops. And it loads in 1/4 the time.
I had tried changing most of the settings but ultimately, the change to 16 bits was all that was required to resolve the problem on two separate computers.

---

