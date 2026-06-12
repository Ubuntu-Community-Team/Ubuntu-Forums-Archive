---
title: "Dual Boot Woes- Vista does not boot after Ubuntu install"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by pitseleh on 2007-10-01
I know there's got to be a zillion of these threads, but I couldn't seem to find one that helped me out.... so sorry ahead of time. Luckily my troubles do not put me in a situation where I'm afraid for my data or completely freaking out over my computer not working proper....

I just purchased a brand new hard drive with the intention of dual booting Ubuntu and Windows Vista. I've had Ubuntu running on my laptop and a few computers all summer, but now I need Windows again for certain classes in school. I've seen so many guides on how to dual boot... but I ended up following this one because it looked very straight forward and pertained to my situation:
[How to dual-boot Vista with Linux (Vista installed first)]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

Unfortunately, my clean install of Vista will no longer boot. When I select it from the boot menu, my computer restarts and just goes back to the boot menu...

I also noticed that now I have two sets of Ubuntu and Ubuntu recovery mode to choose from in the boot menu.

I was just wondering if y'all could point me to a fix or maybe a better way to go about doing this. I'm open to all options.

Thanks!

---

### Post by Nikitas350 on 2007-10-01
First of all post us the menu.lst
(open the terminal and type "gedit /boot/grub/menu.lst")

---

### Post by devosion on 2007-10-01
I used that guide as well and had no problem dual booting. Which choice did you make when it asked you to choose what partition to install Ubuntu on? I had to choose manual and set up the primary and swap partitions manually.

---

### Post by pitseleh on 2007-10-01
I knew I had to post this, but I was not sure how to:
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=7d4977cb-1c77-4170-ba68-72614ed7f983 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7d4977cb-1c77-4170-ba68-72614ed7f983 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7d4977cb-1c77-4170-ba68-72614ed7f983 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=7d4977cb-1c77-4170-ba68-72614ed7f983 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=7d4977cb-1c77-4170-ba68-72614ed7f983 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


I chose to use the "largest continuous space" option because it said that it would install Ubuntu over the space I had left for it on my hard drive.
[IMG]http://apcmag.com/system/files/images/vista_ubuntu_09.preview.jpg[/IMG]

I can see where Vista is on my hard drive- it's still the same size partition and everything. I did notice there is now a "Boot" folder on the Vista partition (it's root C). I'm not sure what that's about or if it's of any use...
[IMG]http://img.photobucket.com/albums/v14/braincandy/Screenshot-Boot-FileBrowser.png[/IMG]

---

### Post by Nikitas350 on 2007-10-04
Sorry for the delay... (i am a student...) So, to fix the problem you have to change these lines (at the menu.lst) :

title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

with these:

title Windows Vista/Longhorn (loader)
root noverify (hd0,0)
savedefault
makeactive
chainloader	+1

or, if this doesn't work try to change the uper lines with these (i don't think that this one will work :(, i think that the first one is more sure so try the up first):

title Vista Ultimate
root (hd0,1)
makeactive
chainloader +1

note 1: to edit the menu.lst type "sudo gedit /etc/grub/menu.lst"
note 2: if this solution does not solve the problem don't give it up. it's a unusual problem so be patient ;). And of course your data will be certaintly not deleted if you just edit the menu.lst... :) Good luck

---

### Post by Nikitas350 on 2007-10-04
[[[[ignore the previous one]]]]]

Sorry for the delay... (i am a student...) So, to fix the problem you have to change these lines (at the menu.lst) :

title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

with these:

title Windows Vista/Longhorn (loader)
root noverify (hd0,0)
savedefault
makeactive
chainloader	+1

or, if this doesn't work try to change the uper lines with these (i don't think that this one will work :(, i think that the first one is more sure so try the up first):

title Vista Ultimate
root (hd0,0)
makeactive
chainloader +1

note 1: to edit the menu.lst type "sudo gedit /etc/grub/menu.lst"
note 2: if this solution does not solve the problem don't give it up. it's a unusual problem so be patient ;). And of course your data will be certaintly not deleted if you just edit the menu.lst... :) Good luck

---

### Post by pitseleh on 2007-10-05
Thanks for getting back to me! I understand how a student schedule goes.. I'm a student myself.

I was able to try those fixes as I understood it, but neither worked, but maybe I'm doing something wrong. :confused:

To edit the menu.lst I typed in "sudo gedit /boot/grub/menu.lst" instead of "sudo gedit /etc/grub/menu.lst" that you described in your post. It brought up a completely blank document. Am I editing in the right location?

I replaced the very last lines of the menu.lst with with each set of lines you provided:

> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
[b]title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
makeactive[/b]


Unfortunately, the first set of lines produced this error.. "Error 11: Unrecognized Device String." The second set of lines just caused it to reboot like it was originally doing.
I'm thinking I'm doing something wrong... so let me know if I'm in the right spot... I really really appreciate the help. Thanks again!

---

### Post by Nikitas350 on 2007-10-05
I didn't mean to change the whole menu.lst. Nevermind to be clear this is your whole menu.lst (changed) :


#start
default 0

timeout 10

title Ubuntu, kernel 2.6.20-16-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=7d4977cb-1c77-4170-ba68-72614ed7f983 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=7d4977cb-1c77-4170-ba68-72614ed7f983 ro single
initrd /boot/initrd.img-2.6.20-16-generic

title Ubuntu, kernel 2.6.20-15-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=7d4977cb-1c77-4170-ba68-72614ed7f983 ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=7d4977cb-1c77-4170-ba68-72614ed7f983 ro single
initrd /boot/initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root

title Windows Vista/Longhorn (loader)
root noverify (hd0,0)
savedefault
makeactive
chainloader +1
#end




so paste it and check it. As for the command "sudo gedit /etc/boot/menu.lst" it was a mistake. So if this doesn't work i can say that i am over ;). The best one thing you have to do (if this doesn't work) is to ask a more expert one (i am newbie one) or to wait 13 days in order to install the new one release of ubuntu :).........

---

### Post by meierfra on 2007-10-05
It should be 

"rootnoverify" and not "root noverify"

---

### Post by Nikitas350 on 2007-10-06
Thanks meierfa. :). I hope you can solve the problem

---

