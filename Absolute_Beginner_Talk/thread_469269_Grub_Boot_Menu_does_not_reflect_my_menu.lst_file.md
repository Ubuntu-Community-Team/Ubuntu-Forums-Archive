---
title: "Grub Boot Menu does not reflect my menu.lst file"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2007-06-09
I have three Ubuntu partitions: /dev/hda1 (an older backup), /dev/hdb2 (a newer backup), and /dev/hda2 (the new partition I plan to use).  Both backups can be deleted once I can get a menu entry that will boot to /dev/hda1.  However, I've edited all my menu.lst entries, none of them effect grub's menu anymore unfortunately.  It has a spelling error in the entry for /dev/hda2 and I've fixed it and refixed and rebooted several times and it's still there.  It's quite frustrating.  

So I tried using grub-install to make grub install itself onto the Master Boot Record.  Here are my results:

> fatsheep:~$ sudo grub-install /dev/hdb2
Password:
The file /boot/grub/stage2 not read correctly.


I've rebooted since then and still the menu is the same and I cannot boot to /dev/hda1.  I'm in need of some help.

---

### Post by Pragmatist on 2007-06-10
Please attach your /boot/grub/menu.lst 

> **fatsheep said:**
> I have **three** Ubuntu partitions: **/dev/hda1** (an older backup), /dev/hdb2 (a newer backup), and** /dev/hda1** (the new partition I plan to use).

I'm confused. You say you have three partitions, but you only list two (/dev/hda1 and /dev/hdb2)  What are you trying to do exactly?

The fact that GRUB got to stage 2 is a good sign.  It almost certainly has to do with the menu.lst

---

### Post by fatsheep on 2007-06-11
> **Pragmatist said:**
> Please attach your /boot/grub/menu.lst 



I'm confused. You say you have three partitions, but you only list two (/dev/hda1 and /dev/hdb2)  What are you trying to do exactly?

The fact that GRUB got to stage 2 is a good sign.  It almost certainly has to do with the menu.lst


Okay I think the boot menu is in line with my menu.lst now but whenever grub updates it edits it incorrectly.  Below are my /etc/fstab and /boot/grub/menu.lst files.  Notice my main partition (/dev/hda2) is listed in fstab but no entry is made in menu.lst.  Also notice that there are entries in menu.lst that are not in fstab.  Why is this? 



Here is my /etc/fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2 /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5 none            swap    sw              0       0
/dev/hda1  /home/fatsheep/old-ubuntu ext3 defaults 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


Here is my /boot/grub/menu.lst after running **sudo update-grub**:

> 
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
# kopt=root=UUID=de1bdd44-22ef-4b4b-978e-df38120e69d7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=de1bdd44-22ef-4b4b-978e-df38120e69d7 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=de1bdd44-22ef-4b4b-978e-df38120e69d7 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.17-11-generic (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=ce21365d-ab2d-4ef8-87f8-46dbd6a011d7 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.17-11-generic (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=ce21365d-ab2d-4ef8-87f8-46dbd6a011d7 ro single 
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title		Slackware Linux (Slackware 11.0.0) (on /dev/hda6)
root		(hd0,5)
kernel		/boot/vmlinuz-ide-2.4.33.3 root=/dev/hda6 
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


---

### Post by Pragmatist on 2007-06-11
> **fatsheep said:**
> ...I've rebooted since then and still the menu is the same and I cannot boot to /dev/hda1.  I'm in need of some help.

Can you boot to /dev/hda1 now??

What are you trying to do exactly?

---

### Post by fatsheep on 2007-06-11
> **Pragmatist said:**
> Can you boot to /dev/hda1 now??

What are you trying to do exactly?

Sorry, that was a typo.  The partition I need to boot to is **/dev/hda2** not /dev/hda1.  I can boot to /dev/hda1, I can boot to windows (/dev/hdb1), but I can't boot to /dev/hda2 unless I manually put in an entry to menu.lst (which gets overrwritten every time grub updates it.  

What I am trying to get grub to recognize /dev/hda2 and automatically put an entry for it in the menu.lst as it has done for /dev/hda1 and the other Ubuntu partitions I've had in the past.

---

### Post by cwmoser on 2007-06-11
> **fatsheep said:**
> Sorry, that was a typo.  The partition I need to boot to is **/dev/hda2** not /dev/hda1.  I can boot to /dev/hda1, I can boot to windows (/dev/hdb1), but I can't boot to /dev/hda2 unless I manually put in an entry to menu.lst (which gets overrwritten every time grub updates it.  

What I am trying to get grub to recognize /dev/hda2 and automatically put an entry for it in the menu.lst as it has done for /dev/hda1 and the other Ubuntu partitions I've had in the past.


I think the boot part of Grub is pointing to /boot/grub/menu.lst on your /dev/hda1 partition and you are editing the menu.lst on your /dev/hda2 partition.

Carl

---

### Post by fatsheep on 2007-06-11
> **cwmoser said:**
> I think the boot part of Grub is pointing to /boot/grub/menu.lst on your /dev/hda1 partition and you are editing the menu.lst on your /dev/hda2 partition.

Carl

Nope, edits I make on my /dev/hda2 partition's /boot/grub/menu.lst effect the boot menu, they are just reversed everytime "update-grub" is run.

---

### Post by Pragmatist on 2007-06-11
> **fatsheep said:**
> Nope, edits I make on my /dev/hda2 partition's /boot/grub/menu.lst effect the boot menu, they are just reversed everytime "update-grub" is run.
Then why are you running "update-grub"!

---

### Post by fatsheep on 2007-06-11
> **Pragmatist said:**
> Then why are you running "update-grub"!

A while back I had a similar problem and I edited the menu.lst thinking it would stay that way but everytime there was a kernel upgrade, I would have to boot to a LiveCD and edit back in my entry.  I posted on the forums and found out that update-grub is run everytime the kernel is upgraded.  I am running update-grub to simulate the kernel being updated.

---

### Post by Pragmatist on 2007-06-11
You need to put your entries in the right place of the menu.lst file.  These pages describe what to do:

[http://users.bigpond.net.au/hermanzone/p15.htm#DEBIAN_AUTOMAGIC_KERNELS_LIST](http://users.bigpond.net.au/hermanzone/p15.htm#DEBIAN_AUTOMAGIC_KERNELS_LIST)

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
[http://www.gnu.org/software/grub/manual/html_node/index.html](http://www.gnu.org/software/grub/manual/html_node/index.html)
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by kittyhawk63 on 2007-06-12
Not "if" but "when" you get your GRUB working again, I would suggest that you make a backup of your GRUB.  

Here is the terminal command for backing up the GRUB:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak

To restore GRUB, type in "recovery mode" during bootup:
sudo cp /boot/grub/menu.lst.bak /boot/grub/menu.lst

Any time you edit GRUB, make sure you redo this back up command. Overwrite the old command. I hope you see a GRUB even though you are having this problem. That is the time you can restore the backup that you prefer.
kh

---

