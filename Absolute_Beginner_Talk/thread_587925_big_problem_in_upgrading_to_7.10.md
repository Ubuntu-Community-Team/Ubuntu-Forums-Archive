---
title: "big problem in upgrading to 7.10"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by afeasfaerw23231233 on 2007-10-23
i am using 7.04 currently. after i click the upgrade button in the update menu, it starts downloading file and working.... then there is a notice pops out saying : not enough free disk space (see the attached screenshot)  i follow its instruction to do the ''sudo apt-get clean '' command. but i get the same result again
 i don't know how to fix this problem.
[[img]http://img3.freeimagehosting.net/uploads/c087fae7c3.png[/img]](http://www.freeimagehosting.net/)
 here's my df -h:


Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb6             112G   92G   15G  87% /
varrun                375M  260K  375M   1% /var/run
varlock               375M     0  375M   0% /var/lock
procbususb            375M  116K  375M   1% /proc/bus/usb
udev                  375M  116K  375M   1% /dev
devshm                375M     0  375M   0% /dev/shm
lrm                   375M   33M  342M   9% /lib/modules/2.6.20-16-generic/volatile
/dev/sdb3              54M   38M   13M  75% /boot
/dev/sdb5              19G   17G  1.4G  93% /home
/dev/sda1              20G   13G  6.3G  68% /media/sda1
/dev/sda5              19G   16G  3.1G  84% /media/sda5
/dev/sda6              19G   11G  8.3G  57% /media/sda6
/dev/sda7              20G   17G  3.3G  84% /media/sda7



any help would be appreciated !

---

### Post by realvz on 2007-10-23
Try "File Systems" tab on "System/Administration/System Monitor".

---

### Post by forestpixie on 2007-10-23
I assume you could remove the old kernels from /boot using synaptic perhaps, have you actually got old kernels in there

Edit - that was a foolish reply, I wil rephrase :)

---

### Post by realvz on 2007-10-23
yeah...try uniinstalling older kernel images

---

### Post by hyper_ch on 2007-10-23
he only got 54MB for his /boot partition...

---

### Post by afeasfaerw23231233 on 2007-10-23
how to remove old kernal? would you give more details?

---

### Post by forestpixie on 2007-10-23
not sure would need to look - but have you actually got any in the directory?

---

### Post by afeasfaerw23231233 on 2007-10-23
yes, i got
here is my /boot/grub/menu.lst
cat /boot/grub/menu.lst
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
timeout         2

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
# kopt=root=UUID=e195351d-8a3a-4ade-b762-ecb3db92a3cf ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd1,2)
kernel          /vmlinuz-2.6.20-16-generic root=UUID=e195351d-8a3a-4ade-b762-ecb3db92a3cf ro quiet splash
initrd          /initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd1,2)
kernel          /vmlinuz-2.6.20-16-generic root=UUID=e195351d-8a3a-4ade-b762-ecb3db92a3cf ro single
initrd          /initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,2)
kernel          /vmlinuz-2.6.20-15-generic root=UUID=e195351d-8a3a-4ade-b762-ecb3db92a3cf ro quiet splash
initrd          /initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,2)
kernel          /vmlinuz-2.6.20-15-generic root=UUID=e195351d-8a3a-4ade-b762-ecb3db92a3cf ro single
initrd          /initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,2)
kernel          /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by forestpixie on 2007-10-23
cd into the directory 

cd /boot/
dir

and post the output

---

### Post by forestpixie on 2007-10-23
> **cheaponline said:**
> i have got same problem, now work it prefectly

so what did you do to get past the problem?

---

### Post by afeasfaerw23231233 on 2007-10-23
wongs@wongs-desktop:/boot$ dir
abi-2.6.20-15-generic             initrd.img-2.6.20-16-generic.bak
abi-2.6.20-16-generic             lost+found
config-2.6.20-15-generic          memtest86+.bin
config-2.6.20-16-generic          System.map-2.6.20-15-generic
grub                              System.map-2.6.20-16-generic
initrd.img-2.6.20-15-generic      vmlinuz-2.6.20-15-generic
initrd.img-2.6.20-15-generic.bak  vmlinuz-2.6.20-16-generic
initrd.img-2.6.20-16-generic

---

### Post by realvz on 2007-10-23
search for 2.6.20-15-generic in synaptics and remove the package

---

### Post by afeasfaerw23231233 on 2007-10-23
or should i burn a ubuntu-live disk to use the diskpartition tool to add more space in /boot?

---

### Post by realvz on 2007-10-23
it depends on you....

diskpartition may be long term thing but it also time consuming...its ur decision...try removing 2.6.20-15-generic 1st

---

### Post by afeasfaerw23231233 on 2007-10-23
there are three:
linux-headers-2.6.20-15-generic
linux-image-2.6.20-15-generic
linux-restricted-modules-2.6.20-15-generic

which one should be deleted?

---

### Post by realvz on 2007-10-23
all of them

---

### Post by forestpixie on 2007-10-23
yopu've got one old kernel that you could remove - can't for the life of me see how you're going to find 30Mb, unless they are that bgi but I don't think so

I really don't know enough to be safely telling you to delete files in there - if you search synaptic for linux-image you should find botht he curent and old kernels - I think if you uninstall it there you should be ok, check for configuration files leftover in synaptic afterwards.

But I would have a good look on the forum for removing old kernels before I did anything.

Edit - he he he slow agin :)

---

### Post by afeasfaerw23231233 on 2007-10-23
oh, no! my cd burner doesn't work. which one should i deleted?

---

### Post by afeasfaerw23231233 on 2007-10-23
then what should i do? @@@@@

---

### Post by realvz on 2007-10-23
linux-headers-2.6.20-15-generic
linux-image-2.6.20-15-generic
linux-restricted-modules-2.6.20-15-generic

and then try upgrading again

---

### Post by afeasfaerw23231233 on 2007-10-23
it seems work. i have 30MB free space in the /boot sector now. it is now downloading file. don't know if it works

---

### Post by afeasfaerw23231233 on 2007-10-24
upgrade sucess, thanks

---

### Post by realvz on 2007-10-24
very good...welcome to gutsy!!!

---

