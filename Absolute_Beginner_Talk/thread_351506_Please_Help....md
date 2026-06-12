---
title: "Please Help..."
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by aabidhussain on 2007-02-02
I have been breaking my head over this for a day now. 
I have tried every possible option to get my ubuntu back in action followed forums ans much more.
I feel like a newbie again even though i've been using ubuntu dapper for a while now.
The problem is Microsoft and the new Windows Vista.. :mad: It ate my lovely Ubuntu's grub following which i have been editing my grub using 3rd party softwares and much more to try and get both working.. I have installed Ubuntu and now i have installed vista.. My Vista is running fine.. But ub\nfortunately now my Ubuntu is not running.. This is my menu.lst file and the Windows lines are added by my. This is the first time i am posting in any forum for help. So please dont disappoint me..

Below you will also find a copy of the fstab file.. 

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
# kopt=root=/dev/sda8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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

title=Windows Vista
rootnoverify(hd0,0)
chainloader +1

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda8 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda8 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin 
boot


### END DEBIAN AUTOMAGIC KERNELS LIST









*****************************************************************************************************************************

FSTAB FILE::::::::::::::::::::::



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda6       /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda9       /media/sda8     ext3    defaults        0       2
/dev/sda7       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by phang on 2007-02-02
I got this off remmelt on [http://ubuntuforums.org/showpost.php?p=117829&postcount=2](http://ubuntuforums.org/showpost.php?p=117829&postcount=2) and this is how I did it when mine broke, so all credit goes to remmelt and grub tools.

> 1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

So [in detail] just boot from the Ubuntu Live CD, and open a terminal.
Type in "grub"
Type in "root (hdx,y)" where x is your hard drive number, and y is your partition. Eg. /dev/hda1 is (hd0,0) and /dev/hdb2 is (hd1,1). In your case its on /dev/sda8, and if you only have your internal and external hard drive, sda is usually (hd1). You can check by mounting /dev/sda8 and "cat [where you your root partition]/boot/grub/device.map" .

And then run "setup (hdx)" where X is your drive that you found out earlier. 
Type "quit"
Then just reboot your machine, and grub should be installed on your MBR.

---

### Post by aabidhussain on 2007-02-02
Hey thanX Phang.. I have tried this.. Like you said my Ubuntu is back but what about my Windows now i am not able to run my Vista.. 
Is there some tweak i need to make so as to run my Vista.. The importance of vista is in the fact that we do a lot of development in Flash so i cant do without it.. Its sad Adobe does not make a Linux version of Flash..
Regards..

---

### Post by Sef on 2007-02-02
> Its sad Adobe does not make a Linux version of Flash..

Flash 9 for Linux just came out.

Dual Boot Ubuntu and Vista:

[Dual Boot 1]("http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx")

[Dual Boot 2]("http://www.ubuntuforums.org/showthread.php?t=212469")

[Dual Boot 3]("http://www.pro-networks.org/forum/about78184.html")

---

### Post by aabidhussain on 2007-02-02
Hey Sef thanks for the help.. But i have gone through all tht.. My grub now shows an error tht the file system type of vista is unkown followed by chainloader  +1 command which was set by me.. 

Is there any other solution avalable to this..??


[QUOTE=Sef;2095192]Flash 9 for Linux just came out.

and buddy thts the flash player you are talking about :) .. However, we use flash for development and unfortunately adobe does not make software for the linux platform.. 

Thanks for all the help guys..

---

