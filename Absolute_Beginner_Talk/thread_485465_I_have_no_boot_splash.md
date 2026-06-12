---
title: "I have no boot splash"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-06-26
When I boot on to my pc I get the grub message then total blackness until the session manager pops up. No text no pretty picture, nothing. At one point I had Ubuntu on my lap top, and when I booted it up there was a Ubuntu splash. I was just curious as to what could cause such a thing to happen. It's not something that just started I've  never had a boot splash. I was never really worried about it just curious really. So if you have any ideas let me know please.

---

### Post by speaker219 on 2007-06-26
once you boot up, go to system > administration > login window
then go to the tab called "local"
make sure you have the style set to "themed" 
and you have a theme picked below that

---

### Post by swoll1980 on 2007-06-26
Not the login screen. The boot slash or text you see inbetween the grub menu,and the log in screen

---

### Post by speaker219 on 2007-06-26
Ehm, do you have "splash" in your grub menu.lst

---

### Post by swoll1980 on 2007-06-27
Where would I find grub menu.lst?

---

### Post by speaker219 on 2007-06-27
> **swoll1980 said:**
> Where would I find grub menu.lst?

/boot/grub/menu.lst

---

### Post by swoll1980 on 2007-06-27
I didn't see anything in there about a boot splash. I attached menu.lst maybe I missed it

---

### Post by swoll1980 on 2007-06-27
There should be an attatchment but I don't think it's on here for some reason.

---

### Post by swoll1980 on 2007-06-27
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
# kopt=root=UUID=5beda2d4-2ab3-4f3f-a6f0-63f09241e501 ro

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
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5beda2d4-2ab3-4f3f-a6f0-63f09241e501 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5beda2d4-2ab3-4f3f-a6f0-63f09241e501 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5beda2d4-2ab3-4f3f-a6f0-63f09241e501 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5beda2d4-2ab3-4f3f-a6f0-63f09241e501 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by swoll1980 on 2007-06-27
Some of the text showed up as smileycons

---

### Post by molly_001 on 2007-06-27
Splash in grub is controlled by a link.
The link has a file extension of .xpm.gz .
You'll need to look in File System --> /boot/grub ... look in that folder for a file names splash.xpm.gz

The link in turn points to a compressed image which is called up during GRUB loading and before the booting of the OS.


On my machines, I have made my own splash.  For instance, on this one the image behind the stark, white letters of GRUB is of my dog.

However, GRUB does not normally *have* a splash.  It's just a text option screen, otherwise black background.  So I am wondering if you are thinking of the actual loading of the ext3 OS.  Which can be "Ubuntu" in 'Fall' colors.

You can remove the 'quiet' tag from the /boot/grub/menu.lst file of the Ubuntu load-up line (in that file) and you'll at least get lots of loading message as Ubuntu comes up.

---

### Post by swoll1980 on 2007-06-27
Where it says "defoptions=quiet splash" remove the   " quiet "  ?

---

### Post by molly_001 on 2007-06-27
no on this line here remove the 'quiet' and two lines below it remove the 'quiet' there also

```
.
.
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5beda2d4-2ab3-4f3f-a6f0-63f09241e501 ro quiet splash

.
.
.
```

---

### Post by jrev on 2007-06-27
H,

You select this line :
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=5beda2d4-2ab3-4f3f-a6f0-63f09241e501 ro quiet splash

and you remove the words quiet and splash if you want to see the actions taken during the boot process

this is what I did on my feisty

---

### Post by swoll1980 on 2007-06-27
Well thats cool at least theres somthing now. Any Idea how I can get my ext3 OS Ubuntu in autum colours going

---

### Post by molly_001 on 2007-06-27
pls list the contents of your /boot/grub file folder

from the terminal you can do:

```
 ( navigate first to    /(root)/boot/grub  )

then issue command

   ls   -l   -R   >   dump.txt

( those are letter L's )
```

and this will  produce a text file called dump.txt in that /boot/grub directory which you can open and copy from.

---

### Post by swoll1980 on 2007-06-27
Permision denied ! I used sudo too so go figure.

---

### Post by swoll1980 on 2007-06-27
from the looks of that command it seems like im trying to make a long list of the grub directory and output the results to a text file called dump.txt is that correct? I will just do it this way

---

### Post by swoll1980 on 2007-06-27
-rw-r--r-- 1 root root   9980 2007-06-14 19:22 xfs_stage1_5
-rw-r--r-- 1 root root 110132 2007-06-14 19:22 stage2
-rw-r--r-- 1 root root    512 2007-06-14 19:22 stage1
-rw-r--r-- 1 root root  10132 2007-06-14 19:22 reiserfs_stage1_5
-rw-r--r-- 1 root root   7860 2007-06-14 19:22 minix_stage1_5
-rw-r--r-- 1 root root   4597 2007-06-20 01:27 menu.lst~
-rw-r--r-- 1 root root   4586 2007-06-27 01:18 menu.lst
-rw-r--r-- 1 root root   9152 2007-06-14 19:22 jfs_stage1_5
-rw-r--r-- 1 root root     15 2007-06-14 19:22 installed-version
-rw-r--r-- 1 root root   8452 2007-06-14 19:22 fat_stage1_5
-rw-r--r-- 1 root root   8660 2007-06-14 19:22 e2fs_stage1_5
-rw-r--r-- 1 root root     15 2007-06-14 19:22 device.map
-rw-r--r-- 1 root root    197 2007-06-14 19:22 default

---

### Post by swoll1980 on 2007-06-27
So what now?

---

### Post by molly_001 on 2007-06-27
Thanks.  Here's the results for the listing directory of my /boot/grub folder.

dino is the name of the dog

Remember now, we are talking here about a GRUB splash -- and not the splash showing when the Ubuntu OS is loading.

```
>
>
>

/boot/grub:
total 304
-rw-r--r-- 1 root root    197 2007-06-16 21:25 default
-rw-r--r-- 1 root root     45 2007-06-16 21:25 device.map
-rw-r--r-- 1 root root  78343 2007-06-20 10:37 dino-zipped1.gz
-rw-r--r-- 1 root root   8660 2007-06-16 21:25 e2fs_stage1_5
-rw-r--r-- 1 root root   8452 2007-06-16 21:25 fat_stage1_5
-rw-r--r-- 1 root root     15 2007-06-16 21:26 installed-version
-rw-r--r-- 1 root root   9152 2007-06-16 21:25 jfs_stage1_5
-rw-r--r-- 1 root root   4935 2007-06-27 00:33 menu.lst
-rw-r--r-- 1 root root   4953 2007-06-20 10:49 menu.lst~
-rw-r--r-- 1 root root   4907 2007-06-20 10:01 menu.lst.bkp
-rw-r--r-- 1 root root   7860 2007-06-16 21:25 minix_stage1_5
-rw-r--r-- 1 root root  10132 2007-06-16 21:25 reiserfs_stage1_5
lrwxrwxrwx 1 root root     26 2007-06-20 10:39 splash.xpm.gz -> /boot/grub/dino-zipped1.gz
-rw-r--r-- 1 root root    512 2007-06-16 21:25 stage1
-rw-r--r-- 1 root root 110132 2007-06-16 21:26 stage2
-rw-r--r-- 1 root root   9980 2007-06-16 21:25 xfs_stage1_5

>
>

```

---

### Post by toedder on 2007-07-18
To get the boot splash screen (well, that progress bar thing between grub and login) activated, you could try to use the StartUp-Manager

```
sudo apt-get install sum
```

You'll find it under Main Menu -> System -> Administration -> StartUp-Manager. You can set up the appearance of your boot process by doing some clicks on a GUI then. Not sure if that helps. Maybe you have somehow not installed any USplash themes. If so, try

```
sudo apt-get install usplash-theme-ubuntu
```

---

### Post by happy-and-lost on 2007-07-18
Has this machine got an onboard Intel graphics card, (865G or similar) by any chance?

For whatever reason, usplash simply will not work with this chipset.

---

### Post by toedder on 2007-07-18
Well, my laptop has an Intel onboard graphics card, and Usplash worked fine for me. It is a 915GM though...

---

### Post by swoll1980 on 2007-07-19
I was playing around with the resolution in the sum program and I got it to work, but it was giving me a unrecignized mode error witch made me hit the space bar a few times to get it going. I went back and tried tinkering with it, and now I can't get it to work again, but now I know it has something to do with the resolution. My resolution is 1024x768 @ 85 hrz but for some reason this does not work during the boot. Anyone have any ideas what I should set this resoluion in sum for?

---

