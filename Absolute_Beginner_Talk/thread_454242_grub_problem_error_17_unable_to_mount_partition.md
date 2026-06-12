---
title: "grub problem error 17: unable to mount partition"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by humbll on 2007-05-25
I had to reinstall windows xp on my machine, i followed the instructions in another thread for reinstalling grub, but now when i attempt to load Edgy I get the error: 17 unable to mount partition. What should I do?

---

### Post by dstew on 2007-05-25
Do you see the grub menu, and then get error 17 when you try to boot Edgy? Does your Windows OS boot properly? If so, it might be an easy fix.

Boot the Ubuntu Live CD. In a terminal type```
sudo fdisk -l
```That will tell us how your partitions are arranged. The next steps get a little tougher. We will need to mount your Ubuntu OS, that is currently on your hard drive, onto the Live CD filesystem that is in the memory. To do this, you need to create a mount point in your Live CD files system, then mount the hard drive file system to the mount point. Once you know what your Ubuntu file system device name is, from the fdisk output, you can mount it. For example, if your Ubuntu hard drive partition is /dev/hda1, then the commands to mount it would be these:```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hda1 /media/ubuntu
```Now that the hard disk system is mounted, you can examine and change the grub menu.lst file. To view it, use```
less /media/ubuntu/boot/grub/menu.lst
```Post the results to the forum, and we can tell you how to fix it.

However, if you are getting this error before you see the grub menu that lets you choose your OS, it is a different problem. Fixable, but different.

---

### Post by humbll on 2007-05-25
sudo fdisk -l

Disk /dev/sda: 38.5 GB, 38502535680 bytes
255 heads, 63 sectors/track, 4681 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2301    18482751    c  W95 FAT32 (LBA)
/dev/sda2            2302        4420    17020867+  83  Linux
/dev/sda3            4421        4681     2096482+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    c  W95 FAT32 (LBA)




ok, i tried to do the other stuff, but when i get to the part where i am supposed to mount the disk i get error for the file system type. Also, according to the info above, it is saying the boot device is my second hdd but it is not supposed to be. there is no OS installed on it, it is an external drive which is only holding files. My Ubuntu partition is sda2, reiserfs. when i mounted it and used the less command, i got file not found. i navigated to the /boot and here is what is there:

ubuntu@ubuntu:/boot$ ls -A
abi-2.6.17-10-generic     System.map-2.6.17-10-generic
config-2.6.17-10-generic  vmlinuz-2.6.17-10-generic
memtest86+.bin
ubuntu@ubuntu:/boot$

Windows XP boots fine..error appears after grub menu is displayed..been up too long, i will check this post later today.. thanks for the help.

---

### Post by OzOle on 2007-05-25
Hi Humbll,

You are not alone with this problem.  :(
I, and many, many others have the same or similar problem, just check the beginners' forum, so there must be something wrong with the system as it is.

I have purchased a USB 60 GB external disk drive on which I intend to run Ubuntu. I can then take it with me and if I can borrow a PC I can load up my personal setup and data without interfering with the PC I am using. A poor man's portable PC  :)

But, alas, I too get **Error 17: cannot mount selected partition**

I do get to see and select from the boot menu before I get Error 17.

I found a link to a free utility program which I downloaded and burnt onto a CD.
It did help me part of the way, but hasn't fully solved my problem.
This is the link:
[http://forjamari.linex.org/projects/supergrub/](http://forjamari.linex.org/projects/supergrub/)

I don't know whether it can help you.

I hope somebody can find a solution and perhaps at the same time get Ubuntu fixed.
It is most frustrating to install the excellent Ubuntu system and then find you cannot even boot up the system.

Good luck and kind regards,

Ole

---

### Post by confused57 on 2007-05-25
Since your filesystem is reiserfs, you'd need to mount this way:
```
sudo mount -t reiserfs /dev/sda2 /media/ubuntu
```

The Super Grub Disk is an excellent idea.

---

### Post by dstew on 2007-05-25
From you fdisk output, you can see that your linux partition name is /dev/sda2. So, your mount command needs to be```
mount -t ext3 /dev/sda2 /media/ubuntu
```The boot flag in the fdisk output is not significant. It only means that a partition can be booted by your BIOS, not that it will be booted. Ignore it.

When you navigated to the /boot directory, you went to the directory of your Live CD file system, not your real Linux /boot directory. You will have to mount the Linux hard disk system first to be able to see it. There is no menu.lst file in the Live CD file system.

EDIT:Confused57 -- wouldn't  the fdisk output say it was reiserfs?

---

### Post by OzOle on 2007-05-25
Hi again, Humbll,

Well, after much searching I found the solution to my problem.
I don't know why or how that problem had come about but at least I have solved it in my case.

Now, I of course don't know whether yours is exactly the same, but I will explain what I did and perhaps that can help you.

1)  I booted up from the pc which runs Xubuntu
     I then plugged in the external USB disk drive which was recognized by the system.

2) I opened a shell terminal and
   typed: [B][I]sudo su
[/I][/B]   followed by my root password  - to become root user

2) typing: ***fdisk -l***
    showed my 2 disks:
    **hda** with its partitions hda1 hda2 hda3 - this is the hard disk in my computer
    **sda**  - this is the USB hard disk with the partitions:
       /dev/sda1  - Windows FAT16 partition
       /dev/sda2  - Linux partition
       /dev/sda3 & /dev/sda5 - the Linux swap partition

3) I typed: ***cd /media/disk/boot/grub***  - the grub directory on the USB disk
    I typed:  ***nano menu.lst***  - nano editor opened the menu which the boot loader looks at during start up
    I scrolled down to the list of boot options (bottom part of the file) and here I noticed that boot file was called **(hd1,1)** (=/dev/sda2 above, don't ask me why) which is partition 2 on the USB disk (the pc hard disk is hd0). There was the problem: the boot file (I think that is the MBR=Master Boot Record (somebody correct me if I am wrong here)) is on the first partition therefore **hd1.1 should be changed to hd1.0**   I did that and rebooted and lo and behold the USB disk started up.

This is what it looks like now:
[B]title    ubuntu .......
root    (hd1,0)
kernet etc etc etc .....
[/B]
To get out of the nano editor type: ***ctrl+x*** and answer ***y*** to saving the changes.

Well, this worked for me.
I hope you can use this info.
Please let me know if it works for you.

Kind regards,
Ole

---

### Post by humbll on 2007-05-25
Ok, here is the output of menu.1st (NOTE: The yellow smiley faces are the number eight within parenthesis, i don't know why they show up as smilies)(NOTE: it is a reiserfs partition, i tried loading it as ext3 and it returned error, it mounted fine as reiserfs, reiserfs is what i made it at install time):

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
# kopt=root=UUID=0781e4d2-26f5-4f0e-ad29-6cb33acc6aec ro
# kopt_2_6=root=/dev/sda3 ro

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
title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows XP Media Center Edition
title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows XP Media Center Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by OzOle on 2007-05-25
Hi Humbll,

I don't know if you understood my previous post and I am not sure we have the same problem. My problem is (was, I found the solution as described): I have a PC with Xubuntu running. I purchased an external USB hard disk on which I wanted to install Ubuntu 7.04. I booted the live CD with Ubuntu 7.04 and had no trouble installing it on the USB disk. BUT when I tried to boot it up I received error 17, the same as you reported. Is our problem the same in your opinion? If so, by studying what I did you might be able to find your own solution. If not, then my chance of helping you is limited as I am no expert on the Ubuntu system setup. Maybe somebody else can help in that case.

To summarize this is what I did:
1) I started up my pc running Xubuntu.
2) Connected my new USB hard disk. The disk was acknowledged and visible.
3) I rebooted my pc with the Ubuntu 7.04 live CD and installed it on the USB disk. There were no apparent problems reported.
4) I have my pc's BIOS set to be able to boot from a USB-HD, so attempted to boot the newly installed Ubuntu 7.04 from the USB hard disk.
5) No go! Error 17.
6) After researching this forum and reading about other people's similar problems and getting an understanding of what might be wrong, I ...
7) booted from the pc hard disk installation of Xubuntu and connected my USB HD.
8 ) I opened a shell terminal window as root and typed: **fdisk -l** which gives a list of all disks whether internal or external connected to the pc at that moment.
9) I then examined the **/boot/grub/menu.lst** of the USB HD (be sure you are looking at the right file because there is a similar file on the pc's internal hard disk with Xubuntu in my case) where it shows how the boot up procedure is trying to boot the hard disk. From this I realized that the setting made by the Ubuntu install program (or maybe some other program, I don't really know) was pointing to the wrong partition on the USB HD. I changed it as described in my previous post. Success! Now I can boot up the USB HD.

I hope this puts you on the right track for what to look for. If you don't understand one or more of the above points or don't know the commands you need to use, then please ask, and if I can help I will. Otherwise somebody else with greater knowledge than me (that wouldn't take a lot) could perhaps help.

Good luck, I'm sure you will find the solution and then be pleased with the result.

Ole

---

### Post by humbll on 2007-05-25
> **OzOle said:**
> Hi Humbll,

I don't know if you understood my previous post and I am not sure we have the same problem. 
My problem is different - i have 2 drives, the usb drive is only to store files, i have the main drive set up to dual boot XP and Ubuntu. I had to reinstall XP (because it was mysteriously wiped almost completely out, there we only a few files on the entire partition), and now i cannot boot into ubuntu. i get the error: 17 cannot boot from partition. I reinstalled grub, but am still not able to access ubuntu, same error. thanks for the posts everyone, if i can't get it fixed i will just reinstall ubuntu. All of my files on the ubuntu partition are still there, but i just cannot boot it up... i posted the menu.1st above, perhaps it will yield clues to the problem..

---

### Post by confused57 on 2007-05-25
> **humbll said:**
> My problem is different - i have 2 drives, the usb drive is only to store files, i have the main drive set up to dual boot XP and Ubuntu. I had to reinstall XP (because it was mysteriously wiped almost completely out, there we only a few files on the entire partition), and now i cannot boot into ubuntu. i get the error: 17 cannot boot from partition. I reinstalled grub, but am still not able to access ubuntu, same error. thanks for the posts everyone, if i can't get it fixed i will just reinstall ubuntu. All of my files on the ubuntu partition are still there, but i just cannot boot it up... i posted the menu.1st above, perhaps it will yield clues to the problem..
In the grub boot menu, highlight your Ubuntu entry, press "e" to edit, then change root to (hd0,1) and in the kernel line to root=/dev/sda2, then press "b" to boot...if it works, this is only temporary but can be made permanent.

---

### Post by humbll on 2007-05-25
> **confused57 said:**
> In the grub boot menu, highlight your Ubuntu entry, press "e" to edit, then change root to (hd0,1) and in the kernel line to root=/dev/sda2, then press "b" to boot...if it works, this is only temporary but can be made permanent.

what exactly do i type to accomplish that? thanks in advance..

---

### Post by confused57 on 2007-05-25
> **humbll said:**
> what exactly do i type to accomplish that? thanks in advance..
I assume you're getting a grub menu when you boot your computer, since you're able to boot Windows.  If you are getting a grub menu, make sure your entry to boot Ubuntu is highlighted, press "e" before the counter finishes counting down.  You'll get a screen with your boot entry:
```
root (hd0,2)
kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro quiet splash
initrd /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot
```

What you would do is highlight the line with root, press "e" again, which will allow you to change the root to (hd0,1), then press arrow down to highlight your kernel line(you may have to press enter first?), then press "e" again to edit the kernel line(change root entry):
```
root (hd0,1)
kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro quiet splash
initrd /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot
```

Once you're made the changes, then press "b" to finish booting your Ubuntu.  I'm not sure I have exact steps you'll need to edit this way, you may have to trial & error to get the entries changed.

If you'd rather, you could go ahead and mount your root partition as you did before then edit your menu.lst:
```
gksudo gedit /media/ubuntu/boot/grub/menu.lst
```
make the changes, quit & save...
then reboot your computer...this would be a permanent edit, until you change it again.

---

### Post by humbll on 2007-05-25
ok it works now, i followed the instructions an have edited the menu.1st file now that i am back in. I was thrown off because when i pressed "e" to edit the second entry (for kernel) all i saw was something like:
<splash

but then i realized i had to press the left arrow to see the rest of the line. I am going to attempt reboot now and see if the changes i made to menu.1st worked. I simply changed all references to root to read (hda1) and all references to kernal to (hda, 2). Thank you everyone for all the help...

---

### Post by confused57 on 2007-05-25
> **humbll said:**
> ok it works now, i followed the instructions an have edited the menu.1st file now that i am back in. I was thrown off because when i pressed "e" to edit the second entry (for kernel) all i saw was something like:
<splash

but then i realized i had to press the left arrow to see the rest of the line. I am going to attempt reboot now and see if the changes i made to menu.1st worked. I simply changed all references to root to read (hda1) and all references to kernal to (hda, 2). Thank you everyone for all the help...

Glad it worked...be sure to change the kopt & groot entries in your menu.lst:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
see the relevant sections in the above grub link

If you don't do this, a kernel update will change your boot entries back to the way they were originally.

---

### Post by Rbchound on 2007-05-28
I get the same error whenever I try to boot to Windows XP with grub.
Ubuntu is on ide 1, 40gb
windows is on raid 0 with 2 sata drives, 80gb each
I have another windows fat32 300gb drive on ide 2
I also have an 80gb external drive via usb.

Here is my fdisk info:

Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19458   156296353+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4661    37439451   83  Linux
/dev/hda2            4662        4866     1646662+   5  Extended
/dev/hda5            4662        4866     1646631   82  Linux swap / Solaris

Disk /dev/hdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       36483   293049666    b  W95 FAT32

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9729    78148161    b  W95 FAT32

Disk /dev/sdd: 4160 MB, 4160249856 bytes
192 heads, 38 sectors/track, 1113 cylinders
Units = cylinders of 7296 * 512 = 3735552 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        1114     4061712    c  W95 FAT32 (LBA)

Can anyone help me configure my grub menu.lst please?

---

### Post by confused57 on 2007-05-28
You'll need to open a terminal and post your menu.lst:
```
gedit /boot/grub/menu.lst
gedit /boot/grub/device.map
```

Raid configurations can sometimes be difficult to boot from grub, but it might be possible.

---

### Post by Rbchound on 2007-05-28
Here they are:

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
# kopt=root=UUID=59050144-4d74-4ee0-8084-0ca7b5fa03b8 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=59050144-4d74-4ee0-8084-0ca7b5fa03b8 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=59050144-4d74-4ee0-8084-0ca7b5fa03b8 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=59050144-4d74-4ee0-8084-0ca7b5fa03b8 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=59050144-4d74-4ee0-8084-0ca7b5fa03b8 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

```
(hd0)	/dev/hda
(hd1)	/dev/hdb
(hd2)	/dev/sda
```

---

### Post by confused57 on 2007-05-28
I don't see a Windows entry in your menu.lst...you can edit your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

Add an entry similar to this at the very end of your menu.lst:
```
title              Windows XP
rootnoverify       (hd2,0)
savedefault
makeactive
map                (hd0) (hd2)
map                (hd2) (hd0)
chainloader        +1
```

---

### Post by Rbchound on 2007-05-28
I am so glad there are people out there that understand and are willing to assist other.
A big KUDO's to you confused57.  Your recommended settings worked like a charm.
Thank you so much.

Happy Memorial Day

Rbchound

---

