---
title: "Error 21"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by wnt22 on 2007-05-09
I just installed Ubuntu on my external hard drive(200 G).  I let the install do my partitions and everything.  When I turn on my computer I get "error 21" from GRUB.  The only way I can get into Linux or Windows is to have the Ubuntu live cd in and then click "Launch from first Hard Disk" (or something like that...  Is there anyway I can fix GRUB so it boots normally?  I have tried looking online for answers, but they seem to difficult for a complete newbie like me.

Thank you.

---

### Post by alienexplorers on 2007-05-09
Did you remove any drives from your system.  Error 21 means grub can't find disk.

---

### Post by wnt22 on 2007-05-09
I don't think I removed any drives.  The error occurs whether or not I have my external hard drive plugged in.

---

### Post by alienexplorers on 2007-05-09
can you run fdisk -l (small L) and print that data here.

---

### Post by drowner on 2007-05-09
Can you show us the output of

cat /boot/grub/menu.lst

and

sudo fdisk -l

---

### Post by wnt22 on 2007-05-09
Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       23944   192330148+  83  Linux
/dev/sdb2           23945       24321     3028252+   5  Extended
/dev/sdb5           23945       24321     3028221   82  Linux swap / Solaris

---

### Post by wnt22 on 2007-05-09
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
# kopt=root=UUID=0c235efb-ec08-40bb-80f2-4748a09cae72 ro

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=0c235efb-ec08-40bb-80f2-4748a09cae72 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=0c235efb-ec08-40bb-80f2-4748a09cae72 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
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
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1




--------------------------------
Is that what you wanted?

---

### Post by alienexplorers on 2007-05-09
When you listed fdisk output I only see one drive with linux on it.  You have in the menu.lst file a drive hd0.0 loading windows.  Your fdisk output does not show any drives with windows on it.  Without a windows disk you will get an error.

---

### Post by drowner on 2007-05-09
> **alienexplorers said:**
> When you listed fdisk output I only see one drive with linux on it.  You have in the menu.lst file a drive hd0.0 loading windows.  Your fdisk output does not show any drives with windows on it.  Without a windows disk you will get an error.

Maybe..

did you sudo fdisk -l ?

or just fdisk -l ?

---

### Post by TheWuse on 2007-05-09
I at one time had the same problem (recently). I fixed the GRUB error 21 by using the Windows XP CD that came with the computer. After inserting the CD, it came to a menu and you were given three options, the option you should choose is "repair"/ "r". Once you've clicked repair it will go through a list commands, once your given the command prompt type "fixmrb" (without the quotes) this should fix your GRUB 21 booting error...

---

### Post by drowner on 2007-05-10
> **TheWuse said:**
> I at one time had the same problem (recently). I fixed the GRUB error 21 by using the Windows XP CD that came with the computer. After inserting the CD, it came to a menu and you were given three options, the option you should choose is "repair"/ "r". Once you've clicked repair it will go through a list commands, once your given the command prompt type "fixmrb" (without the quotes) this should fix your GRUB 21 booting error...

Did that not replace GRUB with the windows bootloader?

---

### Post by wnt22 on 2007-05-10
> **drowner said:**
> Maybe..

did you sudo fdisk -l ?

or just fdisk -l ?

I just did a fdisk -l

Here's sudo fdisk -l
Disk /dev/sda: 100.0 GB, 100030242816 bytes
240 heads, 63 sectors/track, 12921 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6472    48928288+   7  HPFS/NTFS
/dev/sda2            6473       12921    48754440    f  W95 Ext'd (LBA)
/dev/sda5            6473       12921    48754408+   b  W95 FAT32

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       23944   192330148+  83  Linux
/dev/sdb2           23945       24321     3028252+   5  Extended
/dev/sdb5           23945       24321     3028221   82  Linux swap / Solaris
hannaht@hannaht-laptop:~$

---

### Post by wnt22 on 2007-05-10
> 
Quote:
Originally Posted by alienexplorers View Post
When you listed fdisk output I only see one drive with linux on it. You have in the menu.lst file a drive hd0.0 loading windows. Your fdisk output does not show any drives with windows on it. Without a windows disk you will get an error.
Maybe..

did you sudo fdisk -l ?

or just fdisk -l ?


So how would I go about fixing this?

---

### Post by Najand on 2007-05-10
Use the following solution and see if it helps:

Open a terminal in the live CD:

```
mkdir /mnt/root
```

Then mount your partition in it. If you don't know which one it is, then mount any of them, we'll se if it's the correct one.

```
mount -t ext3 /dev/sdb1 /mnt/root
```

You can check if it's the correct one by running ls /mnt/root, which should output something like this :

> bin dev home lib mnt root srv usr
boot etc initrd lib64 opt sbin sys var
cdrom initrd.img media proc selinux tmp vmlinuz

Now that everything is mounted, we just need to reinstall GRUB :


```
grub-install --root-directory=/mnt/root /dev/sda
```

If all went well, you should see something like this :

> Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(sd0) /dev/sda
Now you can reboot and the GRUB menu should appear. If you see a warning message regarding XFS filesystem, you can ignore it.

---

### Post by wnt22 on 2007-05-10
This will work even though I have ubuntu on my external hard drive?  (I just don't want to mess up my computer even more...)

---

### Post by TheWuse on 2007-05-10
> **drowner said:**
> Did that not replace GRUB with the windows bootloader?

Yes, its does replace GRUB with the windows bootloader, but how else do you expect to fix it...once i did that fix it correct my boot problem so i could boot normal as well as off the usb.

---

### Post by wnt22 on 2007-05-10
I just tried doing all of that... but nothing seemed to work... 

ubuntu@ubuntu:~$ mkdir /mnt/root
mkdir: cannot create directory `/mnt/root': Permission denied
ubuntu@ubuntu:~$ mount -t ext3 /dev/sdb1 /mnt/root
mount: only root can do that
ubuntu@ubuntu:~$ /mnt/root
bash: /mnt/root: No such file or directory
ubuntu@ubuntu:~$

---

### Post by Najand on 2007-05-10
How did you install your ubuntu on your external harddisk?
Did you use syslinux to make your usb drive usable?

---

### Post by wnt22 on 2007-05-10
I just used guided install from the Ubuntu disk.  The external hard drive came up as one of the things to use.  So I used the guided option during partitioning and used the whole drive (200gb).  The install made my partitions.  

I don't think I used syslinux, unless the install did it.

Right now I can get to both Ubuntu and XP, but in order to do that I have to have my live CD in and then scroll down the the last option (Boot from first hard disk, maybe?) and then use F6 to type in rescue and then it will allow me to choose whether to run Ubuntu or XP.  But that is a lot of work to get Ubuntu and XP running.

---

### Post by wnt22 on 2007-05-10
I would like to try to reinstall my Windows bootloader but I don't have the XP disk because I got my computer through my university.  How could I reinstall it without the disk? and how do you run it through the USB after you fix it?  Does something just come up or what?

---

### Post by wnt22 on 2007-05-10
Ok I think I might have found something that could help diagnose my problem.

When I do grub:  geometry (hd1)   It comes back Error 21.  

Grub recognizes geometry (hd0) but not hd1.

---

### Post by TheWuse on 2007-05-11
If your still having trouble with that Error 21 here are some links I've found helpful...

[http://http://www.users.bigpond.net.au/hermanzone/p18.htm]("http://http://www.users.bigpond.net.au/hermanzone/p18.htm")

[http://http://ubuntuforums.org/showthread.php?t=431843]("http://http://ubuntuforums.org/showthread.php?t=431843")

---

### Post by wnt22 on 2007-05-11
Thanks for everyone who helped me...

I ended up using SuperGrub to fixmbr (and get rid of GRUB) and then I put GRUB on a spare flash drive and now everything is working!

---

