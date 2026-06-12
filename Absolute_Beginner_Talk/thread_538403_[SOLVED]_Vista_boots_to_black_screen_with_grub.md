---
title: "[SOLVED] Vista boots to black screen with grub"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by Bethrine on 2007-08-29
I installed Dapper Drake and got grub configured to dual boot. Now when I boot into Vista it asks if I want to boot or boot to fix. I have tried both and I get the moving green bars that say Windows Vista underneath and when that is finished I get a blank/black screen. Can anyone help? I have no idea what I'm doing. (The only reason I am running Windows at all is for AutoCAD. I LOVE Ubuntu!)

---

### Post by rsambuca on 2007-08-30
Did Vista ever boot since you started dual booting?  Did you use Vista's own disk partitioner, or the ubuntu one.  If the latter, you will have to reinstall Vista.

---

### Post by Bethrine on 2007-08-30
Dang, I used the Ubuntu one. Is there a way to use Ubuntu to pull files from my old Vista files before I do that? 

My next question will be how do I install Vista with Ubuntu installed first? (I'm happy with a good link here.)

---

### Post by rsambuca on 2007-08-30
Can't you just boot into ubuntu and copy the files from the Vista partition into the ubuntu partition?

---

### Post by Bethrine on 2007-08-30
Probably but I have no idea how to do that.The files I want are family pictures. And I don't know the file names so I would have to search for them.

---

### Post by splintercellguy on 2007-08-30
Does Ubuntu not see the Windows partition? You can definitely do reads from NTFS partitions even without NTFS-3G.

---

### Post by Bethrine on 2007-08-30
I'm afraid the problem is me, there. Disks and gparted (which i don't know how to use) see them just fine.

*edit* what is a read?

---

### Post by rsambuca on 2007-08-30
We will be able to get your pictures.  They will be in a folder called "Documents and Settings" on your Vista partition.

---

### Post by Bethrine on 2007-08-30
wonderful! just point! :) by the way, I do know I have a SATA drive, if that helps any.

---

### Post by rsambuca on 2007-08-30
First, boot into ubuntu.

---

### Post by Bethrine on 2007-08-30
I'm here now, this is my only computer...and hard drive.

---

### Post by rsambuca on 2007-08-30
Does the vista partition show up on your desktop?

---

### Post by Bethrine on 2007-08-30
no, should it?

---

### Post by rsambuca on 2007-08-30
OK, open a terminal (Applications -> Accessories -> Terminal)

enter the following and then post the output here.```
cat /etc/fstab
```

---

### Post by Bethrine on 2007-08-30
:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
:~$

---

### Post by rsambuca on 2007-08-30
```
cat /boot/grub/menu.lst
```

---

### Post by Bethrine on 2007-08-30
:~$ cat /boot/grub/menu.lst
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
timeout         25

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
# kopt=root=/dev/sda3 ro

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

title           Ubuntu, kernel 2.6.15-28-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.15-28-386
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista
root            (hd0,1)
savedefault
makeactive
chainloader     +1
:~$

---

### Post by rsambuca on 2007-08-30
OK, your Vista partition is "/dev/sda2".  What we need to do is to make a directory, and then mount the partition to the new directory.

To make a directory,```
sudo mkdir /mnt/vista
```
Then, to mount the partition,```
sudo mount /dev/sda2 /mnt/vista
```
Let's see if that works!

---

### Post by Bethrine on 2007-08-30
:~$ sudo mkdir /mnt/vista
:~$ sudo mount /dev/sda2 /mnt/vista
:~$


does my Ext3 have errors?  now that I'm really looking at it...?

---

### Post by rsambuca on 2007-08-30
Is it on your desktop now?  If not, what about on your menu bar in Places?

---

### Post by Bethrine on 2007-08-30
no, it never asked me for my password either...??

---

### Post by rsambuca on 2007-08-30
How about ```
cd /mnt/vista
```
```
ls
```

---

### Post by Bethrine on 2007-08-30
:~$ cd /mnt/vista
bash: cd: /mnt/vista: Permission denied
:~$ ls
Desktop  Examples  My Stuff  Pictures  unixstuff
:~$

---

### Post by Bethrine on 2007-08-30
:~$ cd Desktop
:~/Desktop$ ls
evolution-mail.desktop  firefox.desktop  pidgin-2.1.1  pidgin-2.1.1.tar.bz2
:~/Desktop$

---

### Post by rsambuca on 2007-08-30
```
sudo cd /mnt/vista
ls
```

---

### Post by Bethrine on 2007-08-30
:~$ sudo cd /mnt/vista
sudo: cd: command not found
:~$ ls
Desktop  Examples  My Stuff  Pictures  unixstuff
:~$

---

### Post by rsambuca on 2007-08-30
What's going on here!!!

Try ```
cd /mnt
```

---

### Post by Bethrine on 2007-08-30
I've been thinking the same thing, am I in the wrong root/directory or something?

:~$ cd /mnt
:/mnt$

?? is that the created directory?

I'm not certain but I dont think the ~ is familiar in my command line?

---

### Post by rsambuca on 2007-08-30
ahhh, now enter:  ls

---

### Post by Bethrine on 2007-08-30
:/mnt$ ls
vista
:/mnt$

big grin!

---

### Post by rsambuca on 2007-08-30
cd vista

---

### Post by Bethrine on 2007-08-30
:/mnt$ cd vista
bash: cd: vista: Permission denied
:/mnt$

---

### Post by rsambuca on 2007-08-30
This is really ticking me off!  OK, I know what to do.  In a terminal, enter```
gksudo nautilus
```This will open the file browser, but with root privileges.

---

### Post by Bethrine on 2007-08-30
I have four updates I can install, can I do that on another desktop at the same time (by clicking in the lower right hand corner)?

---

### Post by rsambuca on 2007-08-30
Let's find your files first.  It is late and I need sleep!

---

### Post by Bethrine on 2007-08-30
e:/mnt$ gksudo nautilus

(nautilus:8368): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

I have a GUI says root-File Browser at the top too, I don't know how to post screen shots.

---

### Post by Bethrine on 2007-08-30
Oh, sorry, I can meet here at another time? I know how to install the updates, I was just wonder if I should while we are doing this.

---

### Post by rsambuca on 2007-08-30
Great!  That is what we want.  Click File System (on the left), then you will see all of the folders in your root directory.  Click on the 'mnt' folder to open it.  Then click on the vista folder and cross your fingers!

---

### Post by rsambuca on 2007-08-30
You're just lucky that I am a cat lover!  I couldn't resist helping someone with such a great avatar!

---

### Post by Bethrine on 2007-08-30
I believe we are in! It had a lock next to the file, but when I opened it, it worked. Cool!

---

### Post by Bethrine on 2007-08-30
:))

---

### Post by rsambuca on 2007-08-30
Well, what's in the vista folder?

---

### Post by Bethrine on 2007-08-30
Lots of stuff! Documents and settings is there too...Users...I am pretty sure I can navigate to the right folder now!

Yup! found em!!!  Yay!

---

### Post by rsambuca on 2007-08-30
Good stuff!  Just copy and paste 'em into a folder on your ubuntu partition.  You can buy me a beer later!  :guitar:

---

### Post by Bethrine on 2007-08-30
By the way, I tried to pick an avatar that would tell how I really feel about getting stuff done.  Glad it worked!  :):)

---

### Post by Bethrine on 2007-08-30
You got it!!!  Anytime!!!  Thread SOLVED!  Thank you, Thank you! THANK YOU!!!

Now go get some sleep.  :)

---

### Post by mitch_scaff on 2007-09-08
Only one problem - there's no description of how to get vista up and running again from this spot. 

This is the problem I'm facing.  I will search for through a few more threads and see if I can find anyone else who has had the same problem (vista hanging on the crawling green worm or going to black when it's chosen off the boot menu). 

  Yes, I installed ubuntu (6.10) from disk on top of Vista without first using the Vista partition software.

---

### Post by Bethrine on 2007-09-08
Oh, sorry...see here...

[http://ubuntuforums.org/showthread.php?t=542926](http://ubuntuforums.org/showthread.php?t=542926)

---

