---
title: "[SOLVED] Problems with 2 hd and duel booting"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by NovaAesa on 2007-09-29
Hi,

I've been a Ubuntu user for about a month now (and I'm loving it), but after obtaining another 80 GB hard drive I decided I wanted to run a duel boot with XP and Ubuntu. (Before I was doing this as well, but with several partitions on the one drive)

Here's my setup so far:
* Master drive: swap=1.5GiB /home=40GiB /=whatever was left from 80GB
* Slave drive: one large partition for Windows XP about 80GB

I wiped both hard drives (after backing up of course :)) and installed XP first. That all seemed to go well, so then I installed Kubuntu on the second hard drive. This is where the problems started. After installing Kubuntu, I am unable to chose which operating system I want to run at start up. I think Grub is meant to load or something, but it just goes straigt to Kubuntu.

Does anyone know what the problem could be?

---

### Post by Pumalite on 2007-09-29
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by NovaAesa on 2007-09-29
.```
ps@ubuntu-hp:~$ sudo fdisk -lu
Password:

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1       153420750   156360644     1469947+   5  Extended
/dev/hda2              63    78124094    39062016   83  Linux
/dev/hda3        78124095   153420749    37648327+  83  Linux
/dev/hda5       153436815   156360644     1461915   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63   156280319    78140128+   7  HPFS/NTFS
ps@ubuntu-hp:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=832d8161-2251-4ffa-897f-49e0f22be5b6 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=832d8161-2251-4ffa-897f-49e0f22be5b6 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=832d8161-2251-4ffa-897f-49e0f22be5b6 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
ps@ubuntu-hp:~$
```

---

### Post by Pumalite on 2007-09-29
You lack an entry for Windows.
Backup first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back, then:
gksudo gedit /boot/grub/menu.lst
Add at the end (after memtest)

title         Windows 
rootnoverify          (hd1,0)
makeactive
chainloader   +1

Save, exit and reboot.

---

### Post by NovaAesa on 2007-09-29
ok, i can get to the grub menu now and select Windows XP, but when I do so something odd happens. I just get a black screen with white text at the top that says "Starting up...". I waited a while, but nothing seems to happen. There is no hard drive activity either.

---

### Post by NovaAesa on 2007-09-29
bump

---

### Post by logos34 on 2007-09-29
> **NovaAesa said:**
> ok, i can get to the grub menu now and select Windows XP, but when I do so something odd happens. I just get a black screen with white text at the top that says "Starting up...".

You'll need to do a '[virtual swap]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")' of the hard disks if you want to boot windows on the second.

try this entry:

> title	      Windows XP 
root	    (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
savedefault
makeactive
chainloader	+1

Your /boot/grub/device.map should read:
> 
(hd0) /dev/hda
(hd1) /dev/hdb

You also need to make XP partition 'active' by adding a boot flag.  
[B]
gksudo gparted[/B]

choose second disk upper right box

right-click on hdb1>manage flags>check 'boot' box

---

### Post by NovaAesa on 2007-09-29
ok, I did what you said, but it's still not working.

When I tried to boot into Windows, there was a black screen with white text:
> Starting up...
NTLDR is missing press Ctrl+Alt+Del to restart

---

### Post by NovaAesa on 2007-09-29
ok, after a bit of research, it seems to me that I would have been better off originally to install Windows on the first hard drive (master) and Ubuntu on the second (slave).

Would this be correct? (Reinstalling OSs is more in my comfort zone than messing around with Grub, so I'd probably prefer to do that)

---

### Post by jimk0512 on 2007-09-29
I've been successful with dual booting Windows XP and Ubuntu by putting Windows XP on the first hard drive (master), and Ubuntu on the second hard drive (slave) on two different computers. Never could get Windows XP to boot unless it was loaded first on the first hard drive.

---

### Post by handydan918 on 2007-09-29
> **NovaAesa said:**
> ok, after a bit of research, it seems to me that I would have been better off originally to install Windows on the first hard drive (master) and Ubuntu on the second (slave).

Would this be correct? (Reinstalling OSs is more in my comfort zone than messing around with Grub, so I'd probably prefer to do that)

Yes, that is correct. That OTHER O/S doesn't do very well if it knows it isn't on the first drive. 
however, logos34 is also correct, that procedure will work too. 
Look at it like this: if you start futzing around with grub, and you bork it beyond repair, what do you do?
Reinstall.
Why not give it a shot instead of going right to the failure scenario? I guarantee you will learn something. At least about linux and grub, but maybe also about yourself.:)

---

### Post by logos34 on 2007-09-29
["NTLDR is missing, press any key to restart..."]("http://tinyempire.com/notes/ntldrismissing.htm")

Tell me, NovaAesa, is windows (hdb1) mounting in kubuntu and can you see the windows file 'boot.ini'?  If so, what does the 'default' line say? I'm just wondering if 'rdisk' reads 0 or 1 since you installed XP on hdb (slave).

---

### Post by J11Gyro on 2007-09-30
Same here, XP on master 7.04 Ubuntu on slave. Works flawlessly unless daughter has used XP  then we enter a realm of unknown :lolflag: Just for giggles can you change the jumpers on Drives instead of re-install and just do grub rebuild?

---

### Post by logos34 on 2007-09-30
> **J11Gyro said:**
> ...can you change the jumpers on Drives instead of re-install and just do grub rebuild?

yeah, I think that would be the next best solution if novaaesa doesn't want to troubleshoot.  Change root lines in kubuntu menu.lst  to (hd1,2) and write grub to hdb.

---

### Post by dn_desaku on 2007-09-30
A while ago ( a long while ) when I was too chicken to use booter like GRUB I used GAG. Its very simple and easy to set up. Basically fool proof. I stopped using it because I mustered up the bravery to use GRUB and that's when I found out GRUB can use custom backgrounds. :guitar:

---

### Post by NovaAesa on 2007-09-30
ok, after a discussion with a mate of mine, I've just decided to screw the whole duel boot thing and just go with a pure Kubuntu install. My only use for Windows was gaming anyway, after realising that UT2004 has native linux support and I can play Oblivion through Cedega there doesn't seem to be as much of a point using Windows anymore.

Thanks eveyone for helping though!

---

### Post by Pumalite on 2007-09-30
Now you are talking!!

---

