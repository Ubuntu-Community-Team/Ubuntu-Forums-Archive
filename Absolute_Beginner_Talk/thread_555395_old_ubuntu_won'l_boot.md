---
title: "old ubuntu won'l boot"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by Titi on 2007-09-20
hi
yesterday i decided to try sabayonlinux. it turned out to be a disaster. so i configured it NOT to erase my ubuntu installation. that went ok, cause i'm sure it's still there. but "it" installed a different GRUB (i don't know how else to explain this) with no option for ubuntu. i did however add an option for ubuntu myself, which was possible during the installation process, i directed it to the ubuntu partition. anyway, it didn't work. 
so no more ubuntu.
i then started sabayon, but once it was totalle loaded, the screen went white, and i coulnd't do anything anymore. so i guessed: bad install or something.
which left me with no working OS.
then i went to search on this forum, hoping to restore my "old GRUB". i found some methods, involving "setup (hd0,1)", etc.. but none of them seemed to work. or they were just not the solution to my problem.
finally i dug up an old Dapper Drake cd, and installed it, hoping that i'd have my old GRUB back, with the old Ubuntu. and yes, succes! but then when i selected the old ubuntu (which is in fact newer, because it's feisty fawn), it didn't boot. the Ubuntu logo appeared, but then i got a black screen with a blinking cursor, that's all.

so long story short: i's really like my old ubuntu (the feisty fawn) to work again. i'm pretty sure it's still there, i guess it's just a matter of booting it the right way or something. but i'm not at all familiar with this Grub thing, or anything on the computer that's not inside the OS...

any help would be much appreciated. i'd really hate to have to reinstall all my software...

and i'm sure it's quite simple, but i just don't know what to do. 
i have a lot of faith in this forum :-)

maarten

---

### Post by Daveth on 2007-09-20
so, is sabayon still on there? (quite like it myself but only tried it as a live cd). Was this a full hard drive install, and did you play with the partitions beforehand?  
and you say you tried at a terminal prompt

sudo grub
find /boot/grub/stage1
root (    )  - the answer from the above
setup (hd0)
quit

?
Have you explored the supergrub pages?

or is this just a x-server failure, sorted by

[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by quirks on 2007-09-20
Ok, I am a little confused now about what OSs are currently installed on your machine. Is it possible that you provide us with a list of partitions on your hard disk and what OS is installed on which of them? You can do this from your Dapper Live CD using this command:

```
fdisk -l /dev/hda
```

(Hint: hda might not be the correct device, but you probably know it better.)

Can you also give us the contents of /boot/grub/menu.lst (of the GRUB that boots, of course)?

quirks

---

### Post by Titi on 2007-09-20
thanks for the quick replies

i did not explore the supergrub pages, should i?
and i'm sure it's not just X, cause i have no command line or anything, just a "_"

so, sabayon is gone
ubuntu dapper drake is on
my old ubuntu feisty fawn is there somewhere

i have 2 ext3 partitions and 2 swap partitions. this is the fdisk output:

```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/hda

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1           23134       24418    10321762+  83  Linux
/dev/hda2           24419       24792     3004155    5  Extended
/dev/hda3   *           1       23133   185815791   83  Linux
/dev/hda5           24607       24792     1494013+  82  Linux swap / Solaris
/dev/hda6           24419       24606     1510047   82  Linux swap / Solaris

Partition table entries are not in disk order

```

and the menu.lst:

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
# kopt=root=/dev/hda1 ro

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

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.20-16-386 (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=bb529a7a-90de-41c8-8b69-c7208dca7f0c ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.20-16-386 (recovery mode) (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=bb529a7a-90de-41c8-8b69-c7208dca7f0c ro single 
initrd		/boot/initrd.img-2.6.20-16-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.20-15-386 (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=bb529a7a-90de-41c8-8b69-c7208dca7f0c ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.20-15-386 (recovery mode) (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=bb529a7a-90de-41c8-8b69-c7208dca7f0c ro single 
initrd		/boot/initrd.img-2.6.20-15-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.17-11-386 (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=bb529a7a-90de-41c8-8b69-c7208dca7f0c ro quiet splash 
initrd		/boot/initrd.img-2.6.17-11-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.17-11-386 (recovery mode) (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=bb529a7a-90de-41c8-8b69-c7208dca7f0c ro single 
initrd		/boot/initrd.img-2.6.17-11-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.15-28-386 (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=bb529a7a-90de-41c8-8b69-c7208dca7f0c ro quiet splash 
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.15-28-386 (recovery mode) (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=bb529a7a-90de-41c8-8b69-c7208dca7f0c ro single 
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.15-26-386 (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=bb529a7a-90de-41c8-8b69-c7208dca7f0c ro quiet splash 
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.15-26-386 (recovery mode) (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=bb529a7a-90de-41c8-8b69-c7208dca7f0c ro single 
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, memtest86+ (on /dev/hda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, memtest86+ (on /dev/hda1) (on /dev/hda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


```

will that do? i don't know why there's so many of them by the way. this is the one i need (i think) "Ubuntu, kernel 2.6.20-16-386 (on /dev/hda3)"

again, thanks a lot!
i should really learn the basics before doing these things...

---

### Post by Titi on 2007-09-20
ok, so i've searched the forum for similar problems. some one said something about hitting ctrl-alt-F1, so i did. then i saw this message:
"mdadm: No devices listed in conf file were found"
does that have anything to do with my problem?

---

### Post by louieb on 2007-09-20
Well you only have two choices for the feisty install. 
hda3  and hda1. looks like hda3 to me.
add this to the dapper menu.lst

```
title  Feisty on hda3
       configfile (hd0,2)/boot/grub/menu.lst
```See if that will bring up the Feisty installs grub menu.[IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by Titi on 2007-09-20
ok, i did what you said. i now get an extra entry in the grub menu, when i selected, there's a new menu, with basically the same options but in different order. i select the feisty one, but it still won't boot. i get the exact message as before...

---

### Post by Titi on 2007-09-20
after searching the forum again, i found someone with a similar problem. [http://ubuntuforums.org/showthread.php?t=461201&highlight=devices+conf+file&page=2](http://ubuntuforums.org/showthread.php?t=461201&highlight=devices+conf+file&page=2)
kernel tom gives a possible solution, involving the command```
sudo chroot /media/hda3 su
```. when i try this, i get "segmentation fault".
i suspect however that my problem is related to the above one. anyone any idea?

---

### Post by louieb on 2007-09-20
> **Titi said:**
> .... extra entry in the grub menu, when i selected, there's a new menu,...i select the feisty one, but it still won't boot. i get the exact message as before...
Refresh my memory what message? 
The second  menu is the original Feisty menu. Good news that means Feisty is still there. 
The bad news is since it doesn't boot something has changed since you last booted Feisty.
  My wild *ss guess of the day is the **uuid** of the Feisty partition has changed. 
To find the **uuid** of a partition. 
```
ls -l /dev/disk/by-uuid/
```check your menu.lst and /etc/fstab and make sure the uuid's match.

---

### Post by Titi on 2007-09-20
ok, thanks. that last message was "mdadm: No devices listed in conf file were found".

anyway, i'm not home now till sunday, so i hope to fix it then. i may need more help, but i'll post again then.

---

### Post by Titi on 2007-09-22
the UUID's seem to match. 
ok, so when i press crtl-F1, i get the following text on my screen:
```
Booting 'Ubuntu, kernel 2.6.20-16-386'
root (hd0,2)
 Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.20-16-386 root=UUID=bb529a7a-90de-41c8-8b69-c7208dca7f0c ro quiet splash
   [Linux-bzImage, setup=0x1c00, size=0x197aec]
initrd /boot/initrd.img-2.6.20-16-386
   [Linux-initrd @ 0x1f802000, 0x7ddf41 bytes]
savedefault

Loading, please wait...
mdadm: No devices listed in conf file were found

_

```

so i guess that's where it goes wrong...

---

### Post by Titi on 2007-09-24
i really think the problem might be solved by removing mdadm on the feisty partition. but the command "sudo chroot /media/hda3 su" gives a segmentation fault all the time. i have no idea how to solve this. please help me, i'm starting to get desperate...

---

### Post by kernel tom on 2007-10-15
wait i'm confused, which command did you use? 

sudo chroot /media/fiesty su?

or the other one mentioned in your thread?

---

### Post by LowSky on 2007-10-15
>  ```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/hda

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1           23134       24418    10321762+  83  Linux
/dev/hda2           24419       24792     3004155    5  Extended
/dev/hda3   *           1       23133   185815791   83  Linux
/dev/hda5           24607       24792     1494013+  82  Linux swap / Solaris
/dev/hda6           24419       24606     1510047   82  Linux swap / Solaris

Partition table entries are not in disk order
``` 

I thought you can only have 4 partitions on a hard drive and somehow I see 6

---

### Post by patate_fr on 2007-10-26
> **Titi said:**
> i really think the problem might be solved by removing mdadm on the feisty partition. but the command "sudo chroot /media/hda3 su" gives a segmentation fault all the time. i have no idea how to solve this. please help me, i'm starting to get desperate...

I had a similar problem: I couldn't boot and chroot (from several livecd) gave me a segmentation fault.
I copied /lib from another feisty installation and then I was able to chroot and repair the system.
I guess you can copy /lib from a livecd.

system: kubuntu 7.04

---

