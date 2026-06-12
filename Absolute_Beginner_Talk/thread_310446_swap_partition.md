---
title: "swap partition"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by Cardmaster91 on 2006-12-01
hi, i wish that i could use linux as a full time operating system, but im to much of a noob, and its just not compatible with most of my stuff. i want to crerate another partition (windows), but idk how to create a swap partition. is it just free unpartitioned space? or is it something u have to do special? plese point me to a thread or something that could answer me. or you could answer me, lol

---

### Post by cronholio on 2006-12-01
Windows doesn't require a swap partition, if that is what you mean.

Ubuntu does (or prefers to have one) but you probably have created that during your install.

---

### Post by Cardmaster91 on 2006-12-01
is there a way to chek?

---

### Post by Amit Yaron on 2006-12-01
> **Cardmaster91 said:**
> is there a way to chek?

Using GParted: it will show you all the partitions and their sizes.

---

### Post by cronholio on 2006-12-01
```
sudo fdisk /dev/hda
```

I suppose /dev/hda ist your hard disk (first device on first IDE controller).

Then press "p" to show your partitions. "q" quits. Be careful while inside fdisk, or you can mess your system up pretty easily.

---

### Post by LLRNR on 2006-12-01
The swap partition isn't "free unpartitioned space", it's a special partition that's usually 2 * your amount of RAM and it's used for what's called "disk swap", i.e. when your RAM (almost) fills up the OS uses the swap partition for extra space; the swap partition is not primarily used (the best "memory" to use is the RAM), because disk access involves also a mechanical operation and therefore it's a lot slower than accessing your RAM.

Anyway, to install Windows you have 2 options: 

1) use the [GParted LiveCD](http://gparted.sourceforge.net/livecd.php) to resize your current partition and make a new one for your Windows install **+** use [the info in this thread](http://ubuntuforums.org/showthread.php?t=224351) to restore your GRUB from the LiveCD
 
or 

2) run Windoze in a [virtual machine](http://ubuntuforums.org/showthread.php?t=183209).

LLRNR

---

### Post by Cardmaster91 on 2006-12-01
ok, i used gparted and resized hda1. i installed windows on the remaining free space.  but when i boot up my comoputer, it does not ask wat partition i wish to start it in, it just automatically loads windows up.

i remember during the windows installation, it said that it must inactivate or something like that had1 to install windows. i thought, since it said install, it would reactivate it afterwards. this may have something to do with it

---

### Post by LLRNR on 2006-12-01
Ummm... see the second link in my post above, I thought I put it up clear... Windows rewrites your MBR (the place which holds GRUB) and you'll have to use the LiveCD again to restore it.

LLRNR

---

### Post by Cardmaster91 on 2006-12-01
o sory, i didnt see thaat. will it still keep my info though?

---

### Post by LLRNR on 2006-12-01
> **Cardmaster91 said:**
> o sory, i didnt see thaat. will it still keep my info though?

Sure, your actual Ubuntu partition(s) are intact. The thing is, you can't boot Ubuntu because each HDD has a 512 bytes sector called MBR (Master Boot Record). When you installed Ubuntu, it wrote to that sector a reference to GRUB (which is the bootloader), since GRUB itself is too big to fit in that 512 bytes sector... 

The Windows install you did simply overwritten the MBR and now you have to use the LiveCD to write that reference back to your GRUB.

Good luck, just follow that guide and you'll be ok. :)

LLRNR

---

### Post by cronholio on 2006-12-01
What "info" do you mean? It will enable you to boot Ubuntu and Windows but will not touch any of your data, if this is what you mean.

---

### Post by Cardmaster91 on 2006-12-01
ty, that is what i meant, like my music and stuff

---

### Post by ron999 on 2006-12-01
Hi Cardmaster
You were confused, I think.
It's not a swap file you want to create. It's a separate partition to store files to be accessed by both Windows and Ubuntu, kind of a 'shared' partition.
When you've sorted out your GRUB problem you could create this new partition. I think that it's best to format it FAT32 so that both XP and Ubuntu can read and write to it.
Use GParted as LLRNR has suggested.8)

---

### Post by Cardmaster91 on 2006-12-01
ive tried it a few times now, but that thread u gave me doesnt work. i tried that first howto, it seemed to be working, i restarted, and it loaded windows. i tried the second one, and it was unable to find anything.

please help, i have some very important data on my linux partition


here is everything i put into terminal for the first part
(except sudo gpart and quit)

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1 
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

grub> 





and here is what a get for the second howto

ubuntu@ubuntu:~$ sudo mkdir /mnt/root
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda6 /mnt/root
mount: special device /dev/sda6 does not exist
ubuntu@ubuntu:~$ sudo mount -t proc none /mnt/root/proc
mount: mount point /mnt/root/proc does not exist
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/root/dev
mount: mount point /mnt/root/dev does not exist
ubuntu@ubuntu:~$ sudo chroot /mnt/root /bin/bash
chroot: cannot run command `/bin/bash': No such file or directory
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$

---

### Post by Cardmaster91 on 2006-12-01
uhh... well, i tried it once more after i posted that, and it seemed to work, soooo

ron999, u say i should make at a fat32?

---

### Post by LLRNR on 2006-12-01
If you want both read and write access to your new partition, yes, it's best to make it FAT32, since Linux can natively read/write to a vfat filesystem (FAT32). If you'd were to make it NTFS, then you'd only have read access to it (you could of course use some beta-software to have write access too... but it's better to avoid that if it's possible).

LLRNR

---

### Post by ron999 on 2006-12-01
> **LLRNR said:**
> If you want both read and write access to your new partition, yes, it's best to make it FAT32, since Linux can natively read/write to a vfat filesystem (FAT32). If you'd were to make it NTFS, then you'd only have read access to it (you could of course use some beta-software to have write access too... but it's better to avoid that if it's possible).

LLRNR


I agree.:D

---

### Post by Cardmaster91 on 2006-12-01
> **LLRNR said:**
> If you want both read and write access to your new partition, yes, it's best to make it FAT32, since Linux can natively read/write to a vfat filesystem (FAT32). If you'd were to make it NTFS, then you'd only have read access to it (you could of course use some beta-software to have write access too... but it's better to avoid that if it's possible).

LLRNR

ty

---

### Post by Cardmaster91 on 2006-12-02
i just now noticed that windows is not in the menu. it says starting up, press esc to enter menu, i press esc, and it only has ubuntu, ubunu safe, and something (i forgot wat it was, but not windows). i seem to remember one time when i had two os, i dont think u had to push any buttons, the menu would just pop up. But it doesnt it says press esc to enter menu, and it doesnt have windows in it. 
i know windows is still on the computer, because i am transfering some files to my hard drive

---

### Post by LLRNR on 2006-12-02
How does your /boot/grub/menu.lst file look?

---

### Post by Cardmaster91 on 2006-12-02
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
timeout		3

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
# kopt=root=UUID=932fc230-0fcc-41a1-a199-1be59c934d39 ro
# kopt_2_6=root=/dev/hda1 ro

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS ###

---

### Post by cronholio on 2006-12-02
Add this to the end of the file:

```
title           Windows
root            (hd0,1)
savedefault
makeactive
chainloader     +1

```

If (hd0,1) doesn't work, try (hd0,2). It depends on how your HDD is partitioned.

---

### Post by Cardmaster91 on 2006-12-02
di i add it before 
### END DEBIAN AUTOMAGIC KERNELS ###

---

### Post by Cardmaster91 on 2006-12-02
and, do u happen to know how to transfer files from one partition to another?

---

### Post by ron999 on 2006-12-02
Hi

[B]di i add it before
### END DEBIAN AUTOMAGIC KERNELS ###[/B]

It doesn't matter, but afterwards is neater.

**and, do u happen to know how to transfer files from one partition to another?**

Either drag and drop or cut/copy and paste works for me.
8)

---

### Post by Cardmaster91 on 2006-12-02
ok, i guessed, and added it before. but now when i start windows, it loads up with the black screen and loading bar. then shows the blue screen, just before the login buttons appear, and it stays on that scren. it says  microsoft windows xp, and like freezes up. wats up wit dat? 

the only thing i did to the windows partition was add a few files to it, and resize it using gparted

---

### Post by Cardmaster91 on 2006-12-02
> **ron999 said:**
> Hi
**and, do u happen to know how to transfer files from one partition to another?**

Either drag and drop or cut/copy and paste works for me.
8)

umm, well how do i access the windows partioton from say linux or something. )both partitions are on the same hard drive).

---

### Post by ron999 on 2006-12-02
Hi
Well, when I open File Browser, down the left hand side are listed:-

ron
Desktop
File System
Floppy Drive
hda2

hda2 is my shared partition so I can access it from there.

PS, you can't access your Windows partition from there cause it's NTFS.
PPS to move stuff from Ubuntu to Windows do it in 2 moves. First from Ubuntu to shared, then boot Windows and move it from shared to Windows.

---

### Post by Cardmaster91 on 2006-12-02
well how do i transfer files from the windows partition to my ubuntu partition.

and a more pressing matter is i can not loaad windows.

---

### Post by ron999 on 2006-12-02
When you do get Windows to boot....

Copy stuff from Windows to shared partition, then reboot into Ubuntu and copy it from shared to Ubuntu.

---

### Post by ron999 on 2006-12-02
To get Windows to load you could try experimenting with the line you added to  the menu lst.
As cronholio suggested, try either (hd0,1) or (hd0,2).
In my list it is (hd0,0) so try that also.

---

### Post by Cardmaster91 on 2006-12-03
ok, ive solved my windows not loading problem.

now, my windows partition can read the swap. (its fat32). but ubunutu does not dispay it in file manager

---

### Post by ron999 on 2006-12-03
Hi cardmaster
The partition needs to be mounted, I think.

There needs to be an extra line added to your etc/fstab file so that it gets mounted at bootup.
The line in my file looks like this, maybe you can use something similar or Google around:-
UUID=454B-B329  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1

8)

Edit, theres a link here:-[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite")

---

### Post by cronholio on 2006-12-04
@Cardmaster91: Add the Windows boot menu entry **after** the end of the automagic kernel list. If you don't, it will be erased with your next kernel update.

---

