---
title: "Problem With Ubuntu Studio!!!"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by itsvan on 2008-04-17
hi everyone i installed ubuntu studio through the repositories,,and everything seemed fine,,until i restarted my computer and it goes in to the UBUNTU STUDIO loading page,,and then goes into a screen that says my X SERVER. graphics driver or seomthign didnt load up,that it wasnt installed right,,so i had to go in through another selection of ubuntu,,there are like 6 differnt ones,,,what the hell did i DO????????/ as i speak everything seems installed but the problem arises when i restaret the computer,,and im forced to choose another ubuntu boot option,,but it all seems to be the same,,help pleas!!!!!!!!!!!!!!!!!!!!!

---

### Post by itsvan on 2008-04-18
OH ANOTHER THING<<i have two hard drives,,one has UBUNTU,one has WINDOWS XP,,and now i do not see the WINDOWS XP partition,,but i do not think i deleted it,,i mean i cant be that stupid!!!..
what i see is a bunch of other ubuntu partitions,,one goes directly into ubuntu studio,,wich doesnt work,,and the other,,goes into just Ubuntu,,and that's the one im using,,but for some reason its sharing everything same desktop same program just like ubuntu studio,as if its going to the same,,but some how one isnt working,,,,what did i do wrong??/?

---

### Post by alphabyte on 2008-04-18
Have you tried running the restore feature in grub? I personally have had a few problems with "Studio" myself, but not like this. Maybe it just was installed wrong. If you can back up your files and try a clean ISO maybe that would work? Also, did you use 64-bit?
~Alphabyte

---

### Post by itsvan on 2008-04-18
you know i really dont know,,i used some sudo code for repositories,,how can i do that??? by the way,,one of my friends tryied ot reconfigure my x server,,and i dont know what he did,,now none of my effects and other things dont work,,what can i do???

---

### Post by itsvan on 2008-04-18
ok i already fixed the X SERVER PROBLEM,,but i still have that weird boot problem,,i have to selections of ubuntu,,and i cant see my WIndows xp one,,whats up with this?

---

### Post by alphabyte on 2008-04-19
I'd suggest back up what you can and do a clean install off of a dvd
~Alphabyte

---

### Post by alzie on 2008-04-19
Your Grub menu was changed when you updated.

Open a terminal and use the command>  sudo gedit /boot/grub/menu.lst to open Grub in edit mode.  You'll be asked for your password here.

Enter something like 

title		Windows 95/98/NT/2000
root		(hd0,0)
makeactive
chainloader	+1

before the line '### BEGIN AUTOMAGIC KERNELS LIST' if you want Windows as your default OS,  Put it after the automagic section if you want it last.

I think this is what you need here (feel free to copy and paste :) )

I hope this helps :)

---

### Post by itsvan on 2008-04-20
yeh that could be what i have to do,,i have windows xp how do i know what to specifically put in there?,,i dont want to mess anything up, im a nooby ^-^!!!

---

### Post by alzie on 2008-04-22
You use   sudo gedit /boot/grub/menu.lst to open an editing window,  It will ask for your password.

First click File>Save As then change menu.lst to menu.lst.old  You have a backup just in case.

This is from my menu.lst >  # Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

title		Windows 95/98/NT/2000
root		(hd0,0)
makeactive
chainloader	+1


### BEGIN AUTOMAGIC KERNELS LIST

Copy and paste the 4 lines 

title		Windows 95/98/NT/2000
root		(hd0,0)
makeactive
chainloader	+1

By putting this before the AUTOMAGIC section, updates will not effect your windows section in Grub.

Finally click File>Save As and make sure its saved to menu.lst

I think this is what you are looking for :)

---

### Post by itsvan on 2008-04-23
ok i think i can do it,,il post back to see what happens thank you!

---

### Post by itsvan on 2008-04-24
i tried it but it doesnt do anything,,either im doing it wrong,,which might be a possibilit,,or what else is going on??? at the grub screen it still shows all those ubuntu selections,,and i still cant get windows xp to show up,,what should i do now?

---

### Post by alzie on 2008-04-24
Can you post your grub menu.lst?  ( gedit /boot/grub/menu.lst )

we must be missing something here

---

### Post by itsvan on 2008-04-25
most certainly,,here it is


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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=5a1ad86c-8c5a-44bd-8ccb-b2ad7c5218a7 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-rt
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-rt root=UUID=5a1ad86c-8c5a-44bd-8ccb-b2ad7c5218a7 ro quiet splash
initrd		/initrd.img-2.6.22-14-rt
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-rt root=UUID=5a1ad86c-8c5a-44bd-8ccb-b2ad7c5218a7 ro single
initrd		/initrd.img-2.6.22-14-rt

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=5a1ad86c-8c5a-44bd-8ccb-b2ad7c5218a7 ro quiet splash
initrd		/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=5a1ad86c-8c5a-44bd-8ccb-b2ad7c5218a7 ro single
initrd		/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by alzie on 2008-04-25
Ok,  I'm a bit confused.  You said you have 2 Hard drives, One with XP and one with Ubuntu.  Usually in a dual boot windows is on the first drive (C) and other OS would be on the second (D or later) drive.  All your Ubuntus are showing "root (hd0,0)" which is the equivalent of C Drive.  Is windows on the second Hard drive?

Can I get you to post the results from > sudo fdisk -l

---

### Post by itsvan on 2008-04-26
I have to Hardrives,,One has Ubuntu,and one Windows XP,,there both working fine,,but when i want to log into each one i have to go to the set up screen by pressing delete,and have to change manually which hardrive to boot each time,,when i used to be able to select it by pressing escape on the grub menu just before ubuntu would boot up,,now when i choose that it only gives me ubuntu options,,more than they used to be,,and that all happend after i installed ubuntu studio


Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41934192

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6fef6fef

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         124      995998+  83  Linux
/dev/hda2   *         125         610     3903795   82  Linux swap / Solaris
/dev/hda3             611        4865    34178287+  83  Linux
/dev/hda4            4866       10011    41335245   83  Linux

Disk /dev/sdb: 1994 MB, 1994227200 bytes
4 heads, 16 sectors/track, 60858 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Disk identifier: 0xe6093840

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60859     1947479+   e  W95 FAT16 (LBA)

---

### Post by ecrivain5 on 2008-04-26
Hi,
 I am a complete newbie with Linux so I cheated a bit. I downloaded the personal version of "Moka five" and from their extensive library of Linux I downloaded Linux studio. Now when I boot up I boot into windows xp pro and then bring up @moka five@ from there I load linux and can switch easily between the two. I gues it may not be ideal for experts but for me it makes life easy. 
Hope this helps.
Brian:-\"

---

### Post by alzie on 2008-04-26
First we want to backup your menu.lst,  in a terminal type (or copy and paste :) )

> sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old

Now open menu.lst to edit with 

> sudo gedit /boot/grub/menu.lst

Scroll down until you reach this section
> 
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST

Between these two lines we need to type (or copy and paste)

> title		Windows 
root		(hd1,0)
makeactive
chainloader	+1

What this should do is put windows at the top of your grub list (it will be the default OS)  If you want Ubuntu as default put these lines **after **> ### END DEBIAN AUTOMAGIC KERNELS LIST

Save this and close gedit.  When you boot you can use your arrow keys to move to your OS of choice.  

I hope this is what you are looking for.

@ecrivain5,  If it works for you then its right too ;-)

---

### Post by itsvan on 2008-04-26
HI<,ok the code works fine,,and i now see windows as an option,,i set ubuntu as my default boot os,,the only problem i have now,,is when windows is selected,,it goes the the boot screen saying...Starting System or something like that,,but it never moves from there,,its like stuck,,what could this be due to?

---

### Post by alzie on 2008-04-26
Your window's boot loader (mbr) is likely damaged.  I found a link to fix it from within ubuntu tho. [http://ubuntuforums.org/showpost.php?p=4691608&postcount=2](http://ubuntuforums.org/showpost.php?p=4691608&postcount=2)

The alternative is to boot from your windows cd, go into the recovery console and run fixboot and fixmbr from [http://ubuntuforums.org/showthread.php?t=75965](http://ubuntuforums.org/showthread.php?t=75965)

I hope this helps

---

