---
title: "Failed to start the X server."
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by groeswenphil on 2008-02-14
Hi group,

I'm sure that there is something wrong with my instalation. For a start, when I boot up, I see this:-

[IMG]http://www.esnips.com/imageable/medium/ed5ddc3e-a985-41e5-84f9-f62d0f8bc87c/?du=2f5daf47-90d8-49a9-9138-1855fa1248b4&uu=6b519b74-c652-4d38-8ae5-5c31a92cd95c&dt=1202995514000&fu=2b30b777-9409-4a41-a32e-4cf9b7c22cfd[/IMG]

As you can see, it looks like I've four different installations of Ubuntu.

Anyway, I've lived with that for about a year. Normally, I do nothing, or pick the first one and everything works. However, now, if I leave it alone, I get this.

[IMG]http://www.esnips.com/imageable/medium/355e6cb9-7df7-4d7e-8176-2860ee018879/?du=2f5daf47-90d8-49a9-9138-1855fa1248b4&uu=6b519b74-c652-4d38-8ae5-5c31a92cd95c&dt=1202995512000&fu=2b30b777-9409-4a41-a32e-4cf9b7c22cfd[/IMG]

Then this:-

[IMG]http://www.esnips.com/imageable/medium/94bee988-8408-4afc-9e56-f86f94465805/?du=2f5daf47-90d8-49a9-9138-1855fa1248b4&uu=6b519b74-c652-4d38-8ae5-5c31a92cd95c&dt=1202995511000&fu=2b30b777-9409-4a41-a32e-4cf9b7c22cfd[/IMG]

And, if I pick NO, I get this:-

[IMG]http://www.esnips.com/imageable/medium/32a31b42-f593-4394-b279-6a760614c5f0/?du=2f5daf47-90d8-49a9-9138-1855fa1248b4&uu=6b519b74-c652-4d38-8ae5-5c31a92cd95c&dt=1202995510000&fu=2b30b777-9409-4a41-a32e-4cf9b7c22cfd[/IMG]


However, If I pick the second copy of Ubuntu at boot-up, then thankfully, everything works just fine.

How do I get rid of these extra installations,,,,,,,,,,indeed do I need to?
Would it be simpler to just install a newer version of Ubuntu? Currently I use Dapper

Any suggestions?

Phil from Wales

---

### Post by PmDematagoda on 2008-02-14
Could you please post the specifications of your PC.

Also could you please state your problem a little more specifically, what exactly went wrong and when did that start happening.

Also, you do not have multiple Ubuntu's, just one Ubuntu which can be booted with 4 different kernels, you only need to select the latest kernel(the one at the top) since that would normally be the best of the lot, but if you face problems with that kernel then you should select the next one in the list. But do not select the entry just after an entry for a kernel since that will start that exact same kernel up but in Recovery Mode so if the problem is something with the kernel then it may not be solved.

---

### Post by Squizz on 2008-02-14
I'm not sure if they're seperate installs - are the files the same in your /home/ directory?  If they are, then that would suggest that you've just got it repeating in GRUB/different kernels.

Use "sudo fdisk -l" to check and see how many partitions you have.

If you just want to delete them from the grub menu, then edit your "/boot/grub/menu.lst" file and just delete the entries you don't want to see.

---

### Post by porschify on 2008-02-14
Im not sure why your X server isnt working properly.  There must have been something in your newest kernel that isnt playing well with your graphics card.

As for the multiple kernel listings on your boot up  (grub) screen, you can remove them by typing this in a terminal:

```
sudo gedit /boot/grub/menu.lst 
```

Then in that file remove the entries that you do not want to show up on your boot screen.  You definetly should leave your second entry on the list becuase that is your working kernel.  You should also change the default boot order in the file to that of your working kernel.  

My apoligizes for not being able to be more descriptive, but Im on a windows machine right now and cant bring the file up to give a better description.  Maybe someone else can fill in the gaps until I get home.

---

### Post by groeswenphil on 2008-02-14
```
sudo gedit /boot/grub/menu.lst 
```

When I did that, I got this................warning, it's huge:--

Phil

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
# kopt=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu, kernel 2.6.15-51-amd64-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-51-amd64-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-51-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-51-amd64-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-51-amd64-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-51-amd64-generic
boot

title		Ubuntu, kernel 2.6.15-29-amd64-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-29-amd64-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-29-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-29-amd64-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-29-amd64-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-29-amd64-generic
boot

title		Ubuntu, kernel 2.6.15-28-amd64-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-amd64-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-amd64-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-amd64-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-28-amd64-generic
boot

title		Ubuntu, kernel 2.6.15-26-amd64-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by PmDematagoda on 2008-02-14
You do not need to concern yourself with the multiple kernels right now since they are not the ones causing the problem and it is always helpful to have a backup kernel.

Could you please answer the questions I asked in my previous post, then we could get onto fixing this problem:).

---

### Post by jan quark on 2008-02-14
since you can use the terminal

please post the output of 

```
lspci
```

```
sudo lshw
```

---

### Post by bumanie on 2008-02-14
I unfortunately had the same problem yesterday following downloading 4 updates. I could not find any solution other than to reinstall the / file system again.Luckily I had set up a separate /home (although not everything is working perfectly, I have got it working OK). It is obviously something to do with the kernel and the video card. If you installed your video card by stopping x server and stopping gdm via console, I believe that is the cause, when I did it that way I knew there were problems when a kernel upgrade came along, but I didn't realise it would cause me to reinstall.. Installing graphics via restricted driver manager, does not seem to do this. Boot from the previous kernel for the present time . The next kernel upgrade may not do this.

---

### Post by groeswenphil on 2008-02-14
Could you please post the specifications of your PC.

AMD 64 duel core processor........about 1Gb ram.

NVidia graphics.
You know, I built this thing myself and I know that I should know more about it, but because of a problem that it has when it runs Windows, I've never loved this machine.
Ubuntu has always worked fine until a few weeks ago when this problem started. I can't think of anything that I've done that could have caused the problem........if it is a problem at all.

It might help if I could simply remove the first Ubuntu, or move it further down the list.

Thanks,
Phil

Also could you please state your problem a little more specifically, what exactly went wrong and when did that start happening.

Also, you do not have multiple Ubuntu's, just one Ubuntu which can be booted with 4 different kernels, you only need to select the latest kernel(the one at the top) since that would normally be the best of the lot, but if you face problems with that kernel then you should select the next one in the list. But do not select the entry just after an entry for a kernel since that will start that exact same kernel up but in Recovery Mode so if the problem is something with the kernel then it may not be solved.[/QUOTE]

---

### Post by PmDematagoda on 2008-02-14
Could you please post as to how you installed the Nvidia driver in the first place?

---

### Post by bigken on 2008-02-14
at the prompt type 

sudo dpkg-reconfigure xserver-xorg

select nv as your video driver or vesa the go with the defaults

---

### Post by ajgreeny on 2008-02-14
For now boot into the working second kernel (2.6.15-29) and then using synaptic remove the latest but non-working 2.6.15-51 kernel.  Then with the working kernel highlighted in synaptic go to the package menu and select "Lock Version"  You will not now be informed of any updates of the kernel and will be able to continue with the 2.6.15-29 working version.

If you wish, you could also remove the other older kernel versions, 2.6.15-26 and 2.6.15-28, but it is always worth keeping at least one older version on the machine, just in case you should need it in future.

---

