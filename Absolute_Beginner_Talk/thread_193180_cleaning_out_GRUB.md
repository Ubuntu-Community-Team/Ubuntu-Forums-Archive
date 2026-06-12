---
title: "cleaning out GRUB?"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by wog on 2006-06-09
I've done all sorts of things now, and not all of them have been good. Enough are now fixed that I can work with this system, but GRUB now has multiple entries I don't want or don't exist anymore. Is there a way to automagically check/remove the GRUB list for non-working entries? If not, how do I proceed?

---

### Post by brentoboy on 2006-06-09
what all is in there?

post the contents of /boot/grub/menu.lst

we can troubleshoot which ones are "real" and remove the others and then update the grub on your boot sector once we clean it up.

-- if it works, dont fix it -- 
before you start this, you should know that this potentially a hazardous edit to do, but it can be done and it isnt really hard, you just have to preceed with caution.

---

### Post by catlett on 2006-06-09
When you get updates, sometimes you will get new kernels. Grub automatically adds an entry for the new kernel. You can have as many kernels as can fit on your system. Each one can boot and run your system.
You can remove older kernels. You should make sure the new kernel runs without a problem and you should always have a second kernel as a backup boot option.
Kernels can be removed in Synaptic Package Manager. Search under "linux". Just highlight them and choose uninstall.
Or you can keep the kernels and just delete the entries in the grub menu so you don't have to look at them.```
 sudo gedit /boot/grub/menu.lst
``` gets you the grub menu. Either delete the lines with the old kernels or put an "#" in front of the line. "#" tells the computer to ignore the following. This will keep that line from appearing in grub.

---

### Post by wog on 2006-06-09
[QUOTE=brentoboy]what all is in there?

post the contents of /boot/grub/menu.lst

we can troubleshoot which ones are "real" and remove the others and then update the grub on your boot sector once we clean it up.

-- if it works, dont fix it -- 
before you start this, you should know that this potentially a hazardous edit to do, but it can be done and it isnt really hard, you just have to preceed with caution.[/QUOTE]

I've backed up my files. The things I don't know how to backup I'm prepared to lose only if I have to. :p

Here's my menu.lst
I thought there were more options, though.-------------------
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.10-6-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-6-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-6-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-6-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-6-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.10-6-386
boot

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by wog on 2006-06-09
[QUOTE=catlett]When you get updates, sometimes you will get new kernels. Grub automatically adds an entry for the new kernel. You can have as many kernels as can fit on your system. Each one can boot and run your system.
You can remove older kernels. You should make sure the new kernel runs without a problem and you should always have a second kernel as a backup boot option.
Kernels can be removed in Synaptic Package Manager. Search under "linux". Just highlight them and choose uninstall.
Or you can keep the kernels and just delete the entries in the grub menu so you don't have to look at them.```
 sudo gedit /boot/grub/menu.lst
``` gets you the grub menu. Either delete the lines with the old kernels or put an "#" in front of the line. "#" tells the computer to ignore the following. This will keep that line from appearing in grub.[/QUOTE]

What confused me was I installed two kernals because I didn't know which one to choose, and one failed to work. When I finally managed to fight my way around to one that *did* work, I removed the offending kernals through Synaptic, but the kernal entries didn't go away from grub.

Another slightly related problem is I lost gdm because I was having trouble with the nVidia drivers, and didn't know the command line approach to anything. I tried to fix it with the CD and ended up with a second copy of Breezy on my hard drive, which I'm now going to have to find and remove somehow.

Thank you, tho. That makes sense. :)

---

### Post by catlett on 2006-06-09
If your kernels are gone then update grub and it should remove the lines```
 sudo update-grub
``` Then check your menu.
An easy way to make a backup is with cp, so do this first. ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```
Is Breezy on it's own partition? This shows your partitions ```
sudo fdisk -l
```
To fix your gdm or more specific the x window system (gnome is a window manager in the x window system) and change your video drivers etc. run this  ```
sudo dpkg-reconfigure xserver-xorg
``` If you run it while in gnome it will run from the terminal, If you boot in safe mode and run it sudo dpkg..... you will run the setup in a desktop window type of interface.

---

### Post by wog on 2006-06-10
Assured elsewhere that Dapper would install without difficulty, I installed it. The install died halfway through, and after much fussing with it, I did a clean install, wiping the entire hard drive.

Problem solved.

All good command lines, I will keep them in mind for when I attempt to take a slice out of the main partition for my ~/home directory. :)

Sorry I'm so dead-pan, I think I'm still in shock. I am grateful.

---

