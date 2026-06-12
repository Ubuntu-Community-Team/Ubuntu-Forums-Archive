---
title: "failure to install"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by galzion's dad on 2007-09-05
I have an Athlon pc currently running XP on the C drive with the D drive holding the backup of all my data.  There is also another (200GB) hard drive put in specially to try out Linux.
I have tried twice to install Feisty Fawn from an ISO CD, installing it onto the empty drive, with the assumption that ubuntu would spot the Windows OS and set up a dual boot system.
The install seems to go completely - recognises that there is a Windows OS, offers to import user data, writes everything to to designated drive, says it has finished - and then corrupts the mbr on drive 0 so that nothing will boot at all.  Both times I have had to use the XP cd recovery to rewrite the mbr and get XP back.  The ubuntu files are there on the designated drive.
On startup it tells me there has been a Grub failure, error 2.
I rather like the look of Ubuntu but will have to go elsewhere unless I can get a reliable dual-boot system to work.  Any suggestions?

---

### Post by celettu on 2007-09-05
If you can access the ubuntu files, could you post the content of /boot/grub/menu.lst?

---

### Post by mlentink on 2007-09-05
> **celettu said:**
> If you can access the ubuntu files, could you post the content of /boot/grub/menu.lst?

Please boot up with the LiveCD to be able to read your new Ubuntu partition. To assure you, GRUB problems can usually be fixed

---

### Post by galzion's dad on 2007-09-06
Managed it - whoopee for memory sticks!  It is a page and then some, but I don't know what bits matter and what don't so here goes:
The contents of /boot/grub/menu.lst are:

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
# kopt=root=UUID=b09d7a16-579d-4991-80a2-c9abf6d3b37a ro 

## Setup crashdump menu entries 
## e.g. crashdump=1 
# crashdump=0 

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

title		Ubuntu, kernel 2.6.20-15-generic 
root		(hd2,0) 
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b09d7a16-579d-4991-80a2-c9abf6d3b37a ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic 
quiet 
savedefault 

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) 
root		(hd2,0) 
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b09d7a16-579d-4991-80a2-c9abf6d3b37a ro single 
initrd		/boot/initrd.img-2.6.20-15-generic 

title		Ubuntu, memtest86+ 
root		(hd2,0) 
kernel		/boot/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 
root 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/hda1 
title		Microsoft Windows XP Home Edition 
root		(hd0,0) 
savedefault 
makeactive 
chainloader	+1 

I have not tried to reinstall again yet, so cannot remember exactly what error message I got when the machine failed to boot, but obviously I could do that if it would help.  At least I know how to redo the mbr for windows if I need to now!
Very grateful for any help.  There won't be another response from me now until Monday - I've got to go and dig clay for Galzion.  Propably better not to ask.

---

### Post by celettu on 2007-09-07
Error 2 means "selected drive doesn't exist", but it's odd that it gives that error with your XP install too.

The problem has to be the root (hd0,0) or root (hd2,0) lines, or maybe the "root" option in the kernel line...unfortunately, I have no idea how you should edit them.

I'm sorry I can't help.

---

### Post by ed_d on 2007-09-07
hmmmmmm
the kernel line dosent seem right, as in mine, it actually points to /dev/sda1, where as yours points to a uuid number. Look at your /etc/fstab (more /etc/fstab) and see if the uuid number for that drive is the cross reference to the drive in which you loaded ubuntu on. thats a good starting point.

---

### Post by galzion's dad on 2007-09-12
Many thanks for your suggestions and advice.
Since I am really only trying out Linux to see if I can get on with it and wean myself off microsoft I have been trying out other distros as well as Ubuntu.  Having failed miserable with Slackware (disconnected the keyboard and then asked for a key input!) and Gentoo (refused to actually install any files at all) I tried PCLinux, which installed happily, set up a working dual boot system, sorted out an internet connection for me (albeit only through a LAN wire - I still have to get the wifi working), so I will stick with that for the moment.
It's nothing like as good to look at as Ubuntu, though.
Again, thanks, George

---

