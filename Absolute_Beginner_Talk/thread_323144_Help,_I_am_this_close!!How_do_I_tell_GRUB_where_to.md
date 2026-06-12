---
title: "Help, I am this close!!How do I tell GRUB where to look for boot sector?"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by SFGary on 2006-12-21
Disclaimer: Guys, I tried posting this in the laptop group but got no feedback

Based on a recommendation I installed Xubuntu 6.0.6.1 on an old laptop: Toshiba Portege 3480 P3/600 with 192k and a 12G HD, external CD/DVD drive on a docking connector.

The installation from the external CD-ROM went fine and Xubuntu works well when it is docked. However when I undock the laptop and boot the PC it freezes at "mounting root file system" and hangs and after a couple of minutes it says:

"Booting 'ubuntu kernel 2.6.15-26-386
root (hd0,0)
(etc etc)
Uncompressing Linux...Ok booting the kernel.
ALERT! /dev/hde1 does not exist. Dropping to a shell!

Busybox v1.01 (debian....)
/bin/sh: can't access tty: job control turned off
#"
-------------------------------------------------

I am assuming that for some reason the OS is looking for the CD drive but I don't know how to resolve it. Any suggestion would be greatly appreciated.

---

### Post by bulldog on 2006-12-21
Type in your console or terminal,when you're logged in```
sudo fdisk -l (l as in like)
```so we can see your partitions.
Then ```
cat /boot/grub/menu.lst
``` and post this on the forum as well.

---

### Post by dbbolton on 2006-12-21
forgive me if i have misunderstood- if you can't get logged in to xubuntu, then you can run the live cd and use a root terminal to follow bulldog's instructions.

---

### Post by macogw on 2006-12-21
What do you mean "docked"?  It behaves differently when it's in a little holder than when it's on your lap?

---

### Post by SFGary on 2006-12-21
Thanks for the feedback, I'll try what bulldog and dbbolton have suggested.

To magcogw:  The Portege is an ultralight laptop so the CD-ROM can only be accessed via an external dock on a propreitary connector which has a built in CD/DVD rom drive, extra USB ports, network connectors, serial/parallel ports etc. So it was thru this external CD/DVD drive that I installed Xubuntu. So Xubuntu boots fine if the dock (with or without the live CD disc) is connected to the laptop but when I boot without this dock attached then it goes into GRUB, hangs and displays the msg I posted in the previous msg.

Let me try the suggestions and I'll repost, thnx

Gary

---

### Post by confused57 on 2006-12-21
You might also want to post the output of:
```
cat /etc/fstab
```

---

### Post by SFGary on 2006-12-21
I ran xubuntu from the livecd from the ext cd-rom drive and the result (copied everything...):

sfgary@nomdeguerre:~$ sudo fdisk -l
Password:

Disk /dev/hde: 12.0GB, 12072517632 bytes
255 heads, 63 sectors/track, 1467 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device       Boot               Start                        End           Blocks          Id        System
______________________________________________________________________

/dev/hde1     *                     1                        1403      11269566        83         Linux    
/dev/hde2                      1404                         1467       514080           5       Extended
/dev/hde5                      1404                         1467       514048+       82 Linux Swap/Solaris 

sfgary@nomdeguerre:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#                grub-install(8), grub-floppy(8),
                  grub-md5-crypt, /usr/share/doc/grub
#                and /usr/share/doc/grub-doc .

## default num
# Set the dfault entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry 
# is the entry saved with the command 'savedefault'.
#WARNING: If you are using dmraid do not change this entry to 'saved' or your 
# array will desync and will not let you boot your system.
default            0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout            3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

#pretty colours
#color cyan/blue white/blue

## password ['--md5']passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
@ command 'lock'
 e.g. password topsecret
#     password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title                 Windows 95/98/NT/2000
# root                 (hd0,0)
# makeactive
# chainloader       +1
#
# title                Linux
# root               (hd0,1)
# kernel            /vmlinuz   root=/dev/hda2 ro
#

#
# Put static boot stanzas before d/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for the automatic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt+root=/dev/hda1 ro
##       kopt_2_6_8=root=/dev/hdc2 ro
##       kopt_2_6_8_2_686=root/dev/hdc2 ro
# kopt=root/dev/hde1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##       alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative= true
##       lockalternative=false
# alternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions= quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##       altoptions=(recover mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##        howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##        memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## End Default Options ##

title           Ubuntu, kernel 2.6.15-26-386
root          (hd0,0)
kernel       /boot/vmlinuz-2.6.15-26-386 root=/dev/hde1 ro quiet splash
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root           (hd0,0)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/hde1 ro single
initrd          /boot/initrd.img-2.6.15-26-386

title           Ubuntu, memtest86+
root           (hd0,0)
kernel        /boot/memtest86+ .bin
boot

###END DEBIAN AUTOMATIC KERNELS LIST
sfgary@nomdeguerre:~$

--------------------------------------------------------------------------------------

---

### Post by SFGary on 2006-12-21
to confused 57: here it is:

sfgary@nomdeguerre:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#<file system>  <mount point>    <type>     <options>       <dump>    <pass>
proc                   /proc                  proc         defaults            0               0
/dev/hde1          /                         ext3         defaults,errors=remount -ro 0       1
/dev/hde5          none                   swap         sw                   0               0
/dev/hdc           /media/cdrom0     udf,iso9660  user ,noauto   0               0
sfgary@nomdeguerre:~$
-------------------------------------------------------


thanks for trying to help :)

---

### Post by confused57 on 2006-12-21
Evidently when your computer isn't docked, it changes the device drive designation in Linux...what you can try, and it'll take a little trial & error, is to highlight the Ubuntu entry in the grub menu, press "e" for edit and try changing the kernel line root=/dev/hde1 to hda1, hdb1, hdc1, etc...this change is only temporary, so you won't be affecting your grub menu.lst in your installation.  If you're able to boot Ubuntu by changing the root device in the kernel line then you can make it permanent in your /boot/grub/menu.lst to boot without your computer being docked...however, it may not boot if your computer is docked...might be best not to make it permanent, but hopefully this will allow you to boot undocked, by editing the root device in the grub menu at boot.  Good luck.

---

### Post by SFGary on 2006-12-21
confused57, I apologize in advance. How do I do what you suggest: *highlight the Ubuntu entry in the grub menu, press "e" for edit*?

I am still booted in from my previous experiment from the live CD should I continue from that ubuntu command line or should I shut down, disconnect the dock and reboot and try from here?:
---------------------------------------
 "ALERT! /dev/hde1 does not exist. Dropping to a shell!

Busybox v1.01 (debian....)
/bin/sh: can't access tty: job control turned off
#"
----------------------------------------

I still belong to the uninitiated class of linux users]:confused:

---

### Post by confused57 on 2006-12-21
> **SFGary said:**
> confused57, I apologize in advance. How do I do what you suggest: *highlight the Ubuntu entry in the grub menu, press "e" for edit*?

I am still booted in from my previous experiment from the live CD should I continue from that ubuntu command line or should I shut down, disconnect the dock and reboot and try from here?:
---------------------------------------
 "ALERT! /dev/hde1 does not exist. Dropping to a shell!

Busybox v1.01 (debian....)
/bin/sh: can't access tty: job control turned off
#"
----------------------------------------

I still belong to the uninitiated class of linux users]:confused:

Yes, my intention was for you to try booting & editing the grub menu with the pc disconnected from dock...press "esc" within 3 seconds(when prompted) to access your grub boot menu...your Ubuntu boot entry should already be highlighted, press "e", which will bring up a screen to edit any of the parameters(specifically your root=/device/hd??),
then I think you press "b" to boot(read the menu options at the bottom)...this may or may not work to boot with your pc not docked.

---

### Post by SFGary on 2006-12-21
confused57 you rock!!! hda1 works!!!  also the freaking wireless works right off the dang box. So how do I make it permanent? xubuntu is amazingly fast in this old machine.

---

### Post by confused57 on 2006-12-21
> **SFGary said:**
> confused57 you rock!!! hda1 works!!!  also the freaking wireless works right off the dang box. So how do I make it permanent? xubuntu is amazingly fast in this old machine.
You need to edit your /boot/grub/menu.lst.

Open a terminal(Applications---Accessories---Terminal), copy&paste each line one at a time, press "enter" after each line:

```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo nano menu.lst
```

The first line changes to your grub directory, the 2nd line creates a backup file, and the 3rd line opens your menu.lst file so that you can edit & make changes.

As I mentioned, if you boot with your pc dock connected, you may have to change the root device to hde1(temporarily, as I described earlier) in order to boot Ubuntu.  Glad it worked.

If you need to restore your backup:
```
sudo cp menu.lst_backup menu.lst
```

Edit:  Since you're using Xubuntu, you'd need to use nano instead of gedit...also, the "open a terminal" will be slightly different...easy to find, though.

Add:  Rather than bump the thread...I believe you'll catch on quickly to using (X)ubuntu, there is definitely a learning curve(read as much as you can, "play" around with the OS, and don't hesitate to ask questions in the forum)...thanks for letting me know it worked, especially your WiFi...you'll be helping out here before you know it.   Later...

---

### Post by SFGary on 2006-12-22
confused57, thanks a bunch for your patience and help. I got it to work. It looks like there's a whole lot of learning to happen for me to be useful w/xubuntu. At least I won't need help w/getting Wifi to work :) I have to see what other apps I can get to work.  Again, thnx very much.

Gary

---

### Post by confused57 on 2006-12-22
Gary,
   There's a line in your /boot/grub/menu.lst that may reset all your root=/dev/hda1 back to root=/dev/hde1 if you happen to update your kernel:

# kopt=root/dev/hde1 ro

What happens is that during a kernel update, update-grub is run and this line is used to set your device root, as described here:

[http://users.bigpond.net.au/hermanzone/p15.htm#kopt](http://users.bigpond.net.au/hermanzone/p15.htm#kopt)


I just wanted you to be aware of this, because I believe there is a kernel update available...least you know how to edit your /boot/grub/menu.lst to correct any problems.

---

