---
title: "Cannot Boot After Install Using nVidia SATA/RAID"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by shane.gardner on 2006-12-15
I am new to ubuntu and somewhat skilled with Linux (not much, but enough to be dangerous).  I am trying to install 6.06 LTS x64 version on a Gigabyte board.  When I installed WinXP before I remember having to load SCSI drivers during the initial install.  Also, I should point out that for some reason I had to use the nVidia RAID in order to get WinXP to see my drive.  So now I am installing ubuntu, I left the boot SATA drive as a stripe RAID.  I get through the LiveCD install (note I had to choose safe graphics and 1024x768x32 display or else screen is garbled) and the install is complete.  Pop the CD out and re-boot... nothing.  My computer posts and then sits there at a blinking cursor.  No error message.

Note that before I installed I ran liveCD and mounted this drive as NTFS read-only and copied my WinXP data to another IDE drive that I formatted ext3.  So I know I can read the drive.  

I read something on other posts about the boot not getting written properly.  I also read some  post about all kinds of bad things about getting ubuntu to "see" the RAID drive for boot purposes.

Can someone help me.  I completely wiped my WinXP so now I only have the liveCD to get to the outside world!  Thanks!!!!

UPDATE

I booted again from the CD.  I tried the option "boot from hard disk."  It displayed something and then "GRUB."  Again it just hanged.  I went back and mounted the root partition.  I went to find the grub menu.lst.  Here is what I got:

> root@ubuntu:/media# mount /dev/sda1 /media/sda1
root@ubuntu:/media# ls
sda1
root@ubuntu:/media# cd sda1
root@ubuntu:/media/sda1# ls
bin    dev   initrd      lib32       media  proc  srv  usr
boot   etc   initrd.img  lib64       mnt    root  sys  var
cdrom  home  lib         lost+found  opt    sbin  tmp  vmlinuz
root@ubuntu:/media/sda1# cd boot
root@ubuntu:/media/sda1/boot# ls
abi-2.6.15-26-amd64-generic         memtest86+.bin
config-2.6.15-26-amd64-generic      System.map-2.6.15-26-amd64-generic
grub                                vmlinuz-2.6.15-26-amd64-generic
initrd.img-2.6.15-26-amd64-generic
root@ubuntu:/media/sda1/boot# cd grub
root@ubuntu:/media/sda1/boot/grub# ls
default        fat_stage1_5  minix_stage1_5     stage2
device.map     jfs_stage1_5  reiserfs_stage1_5  xfs_stage1_5
e2fs_stage1_5  menu.lst      stage1
root@ubuntu:/media/sda1/boot/grub# cat menu.lst
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
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title           Ubuntu, kernel 2.6.15-26-amd64-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.15-26-amd64-generic
boot

title           Ubuntu, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

Can anyone PLEASE help?  Thanks a lot!

---

### Post by psusi on 2006-12-15
Are the two disks in the raid the only two in the system?  If so then it looks like you clobbered your existing data on the disks because you now have a filesystem on only one disk ( /dev/sda ).  Also the references to hd2 in menu.lst should be hd0.  

You might want to read up on [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

---

### Post by shane.gardner on 2006-12-15
Actually, there are 4 drives.  

hd0 - IDE (currently a bad NTFS partition)
hd1 - IDE (wiped it)
hd2 - first SATA (the one I have as boot in bios)
hd3 - second SATA (ext3 partition, where I put all my WinXP data for migration)

I really think it is related to the RAID.  I think ubuntu can talk to the drives just fine.  Its just it can't boot right from it for some reason.

By the way, I ran some diagnostics using the Ultimate Boot CD.  One of them will let you try to boot partitions.  I got this error:

/boot/vmlinuz-2.6.15-26-amd64-generic initrd.img-2 error 0x35BE loading file error 0x4 loading file

Maybe it is a clue.  I will look into the fake raid...

---

### Post by shane.gardner on 2006-12-17
*************  RESOLUTION  ************

Okay.  I finally can now boot from the hard disk.  Here is the resolution I found.

First of all, my mobo is a Gigabyte GA-K8NF-9.  I discovered two major problems:

1.  I have to add SATA drives to the RAID list.  If not, GRUB (actually they will not show up in the boot list in the BIOS) will not see the drive at boot time.
2.  The hard drive order at boot time is not necessarily the same as what you see when running LiveCD.

I installed my ubuntu to my first SATA drive.  When you run LiveCD, setup sees the drive as hd2 (third disk) because I have two IDE drives before the SATA.

** Here is the important thing.  At boot time GRUB apparently sees the hard disks in the order they appear in the BIOS boot order (for my board, go into advanced settings and you can set the hard disk boot order).

What I had to do to solve the problem is:

NOTE:  All of this assumes you already went through the ubuntu install process.

1.  Boot into LiveCD
2.  Create a small partition in the first IDE drive you can boot from.  I did this by running fdisk, creating a small (I chose 128 MB, but I think it can be as small as say 20 or 30 MB).
3.  Format the partition.  I used mke2fs to format.
4.  Mount the partition.
5.  Mount the ubunu install partition.
6.  Copy /boot from ubuntu to the small partition on the IDE drive.
7.  Run GRUB from a terminal...
       >find /boot/grub/stage1  (you will get the disk/parition where ubuntu is... e.g. (hdX,Y)
       >root (hdX,Y)
       >setup (hdZ) where Z is the disk number for the first IDE (see 2 above)
8.  Edit menu.lst in /boot/grub on this first IDE drive you are going to boot from.  Change all the (hdX,Y) to (hd1,Y).
9.  Reboot.  Go into your bios.  Go to advanced settings.  Go to hard disk boot order.  Make the "hdZ" drive the first drive.  Make the "hdX" drive the second one.
10.  Reboot.  You should now finally be able to boot!!!!! 

If you deciphered the above you may now be wondering why I didn't make the "hdX" the first boot drive and just change all the (hdX,Y) to (hd0,Y).  Well, the answer is I tried that and it still didn't go.  For some reason GRUB cannot start from my SATA drive.  So the only way I found is to fool it by putting GRUB on an IDE drive and pointing to the Linux image on the SATA drive.

I hope this helps someone.  I apologize for the poor description about, but it is like 5 AM and I am about to pass out.

---

