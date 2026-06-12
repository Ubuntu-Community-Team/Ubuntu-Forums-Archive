---
title: "Hard Drive setup w/ one IDE and one SATA drive"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by neatokino on 2008-02-13
This is probably a BIOS setting question, but I'm stumped here and could use some help.  I have been running Gutsy with a Gigabyte GA-EP35-DS3P motherboard;  I've installed the OS on a Seagate 250GB internal IDE hard drive, and everything has run perfectly.  

I'm now trying to add an internal Western Digital 750GB SATA drive on which to store music/media/backups.  I've physically installed the drive, and formatted it with one ext3 primary partition,  BUT when I boot up the computer, it seems to want to boot on the 750GB drive (which has no OS on it), and the computer just hangs after GRUB loading and leaves me with a black screen.   

If I hit F12 during bootup and tell the BIOS to start with the 250GB drive, the computer boots as it should and the 750GB drive mounts.  However, I can't seem to find a way to set the BIOS defaults so that it AUTOMATICALLY boots from the 250GB drive.  It seems to recognize both drives as 'Master' and won't start with the 250GB drive unless I explicitly tell it to during bootup.

I think what I want is for my system to see the 250GB IDE drive as Master and the 750GB SATA drive as the 'slave'--- right???

Can anyone help me figure out how to designate the 750GB SATA drive as the 'slave' to the 250GB IDE drive?  There are no jumpers set on the 750GB drive, but as far as I can tell from the Western Digital site, there is no jumper configuration that makes the drive into a 'slave'.

TIA

---

### Post by Blutack on 2008-02-13
Hang on, is grub on the 750 or 250?
From the way you describe it
> BUT when I boot up the computer, it seems to want to boot on the 750GB drive (which has no OS on it), and the computer just hangs after GRUB loading and leaves me with a black screen.
It sounds like grub is loading off the 750.

---

### Post by neatokino on 2008-02-13
GRUB is on the 250GB drive.  I partitioned the 750GB drive as an ext3 primary partition.  Should I have called it a 'logical' partition?   If GRUB is reading off the 750GB drive, how do I change that?  Thanks for your help... these things are still very confusing to me!

---

### Post by Shazaam on 2008-02-13
What Blutack said. If you have done a kernel update grub was probably put on the 750. One way to tell is to disconnect the IDE drive and see if the grub screen shows up.

Does your motherboard use "pseudo-SATA"? My Soyo board does and the SATA drive is recognised as SCSI in the boot order. With mine it uses a raid chip on the board to control SATA compatability. Roam around in the bios and see if yours is like this. I did the exact opposite as you. I had Win XP on the SATA drive and Ubuntu on an IDE (PATA) drive. I got to the point where I only used XP for gaming so I switched the O/S's around so Ubuntu (and other linux distro's) is on the SATA (320gig) drive now.

---

### Post by neatokino on 2008-02-13
Now I'm totally confused!  In any event, I know that there has been no update since I put the drive in (I took it straight from the newegg box, installed it in the computer, partitioned it with Gparted, and fired it up), so the only way GRUB could be on it is if GRUB got put on when I partitioned the drive.  Is that possible?

There is a place in the BIOS settings where I can specify which drive is to be recognized first.  I have always had  that set to be the 250G drive, but it doesn't seem to matter.  For some reason, it sees both drives as 'Master' and tries to start off the 750G drive first anyway.   There must be some way to get my system to see the 750G drive as just an extra drive for storage, right?

Any thoughts?

---

### Post by mrsteveman1 on 2008-02-13
With sata there is no master/slave because SATA is entirely point to point.

Your bios should in fact have a place to designate the boot order of the drives. For instance mine lets me order the installed drives for boot regardless of how they are connected.

---

### Post by Moop on 2008-02-13
> **mrsteveman1 said:**
> With sata there is no master/slave because SATA is entirely point to point.

Your bios should in fact have a place to designate the boot order of the drives. For instance mine lets me order the installed drives for boot regardless of how they are connected.

So it would be normal for both of your drives to be master and that doesn't hurt anything. When you switch the order that your drives boot in the bios make sure that you are saving your settings when exiting the bios.

---

### Post by neatokino on 2008-02-13
Thank you all for your suggestions, but it's still not working.  It's baffling to me.  I've taken the 750G drive out, and the computer works fine.  But when I put the 750G drive back in and press 'delete' on startup to configure the BIOS to automatically boot off the 250GB drive first, it posts, then enters GRUB, then gives me a black screen. 

On the other hand,  If I press F12 while booting and then get a (one time only) boot-order menu, I can choose the 250G drive, and Gutsy starts, and the 750G drive mounts.  It's really strange.

I'm guessing here, but does this have anything to do with the partition on the drive being 'primary' or 'logical'?  Any other suggestions to try?

---

### Post by mrsteveman1 on 2008-02-13
So regardless of what you do (if you just let it boot normally, no F12), it loads grub right?

What does the kernel line say about root=  ? Is the system trying to root itself from the wrong drive?

Unless you have more than 4 partitions on a drive you always want them to be primary partitions.

You may also try adding edd=off to the kernel line, since some systems refuse to boot correctly without it. Usually these are systems with an add-in PATA card but it could apply here as well.

---

### Post by neatokino on 2008-02-13
Thanks for your response, Steve.  Unfortunately, I'm newbie enough not to know how to check things or change things in the kernel.

**Yes, regardless of what I do, it does load GRUB**. 

*What does the kernel line say about root= ? Is the system trying to root itself from the wrong drive?* 

 [B]uh... I don't know how to find the kernel line... can you give me a step-by-step on doing this?
[/B]
*You may also try adding edd=off to the kernel line*

[B]Could you also give me a step-by-step on how to do this and how to change it back if it doesn't work?
[/B]

Thanks so much!

PS:  is my problem likely to be solved if I get a SATA drive to replace the IDE drive?  250G SATA's are reasonably cheap these days...

---

### Post by Therion on 2008-02-13
I was having similar problems when I was trying to use mixed drives and dual boot.  GRUB, I have been informed, is programmed to privilege PATA over SATA.  This being the case, it checks the IDE channels first and, if any drives are present, assumes the first one is the boot drive *regardless of the BIOS hard disk boot priority.*  

What I did was simply install Ubuntu on the SATA drive while the IDE drive was *physically disconnected* from the motherboard.  Once the install was complete, updated etc. I plugged in the IDE slave-drive, immediately went into the BIOS and checked that both drives were being recognized correctly and that the boot order was correct.  That solved the problem for me.

---

### Post by KCormier on 2008-02-13
Can you post up a copy of /boot/grub/menu.lst ? :)  open up xterm and run

```
more /boot/grub/menu.lst > ~/Desktop/menu.lst.txt
```  :)  then you can just open the text file and paste it here! :-D

PM me once you post it! :-D

---

### Post by neatokino on 2008-02-14
**OK, here's what I got:**  (oh and btw, only the 250G drive was installed when I ran this, as I've taken the 750G drive out for now)


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
# kopt=root=UUID=9ba02aa3-0349-4df3-ab41-e8054a37492a ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9ba02aa3-0349-4df3-ab41-e8054a37492a ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9ba02aa3-0349-4df3-ab41-e8054a37492a ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by hyper_ch on 2008-02-14
You should have a setting in the BIOS where you can define the boot order. I have that one. I can boot from any master/slave primary/secondary or SATA drive (here, I can only say to give SATA priority over IDE)

---

### Post by neatokino on 2008-02-14
I set my 250GB IDE drive in the BIOS as the first drive in the boot order, but that doesn't seem to help!

---

### Post by hyper_ch on 2008-02-14
In my bios I had an option whether to boot from usb/other devices... those other devices are also the SATA drive. I have the option in there for disabling that. Maybe that helps.

---

### Post by KCormier on 2008-02-14
sata drives always take precedence over ide drives.  Hence when he puts in the sata drive it becomes hd0 and the ide drive becomes hd1.  Then his menu.lst points to the incorrect drive (trying to boot off sata drive) and it won't start.  I asked for his menu.lst before but he pm'd it to me so i'll be including an updated copy.

neatokino, first i want you to open a console (hit ctrl+f2 and run "xterm")
run "sudo gedit /boot/grub/menu.lst"
delete the old stuff and paste the code below (it's your old code w/ a few additions)
Shut down, add the sata drive, and then when you start up, pick the boot option that starts with hd1 :)  If it works, let us know and we'll fix your menu.lst so it looks normal but all works right!

```

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=9ba02aa3-0349-4df3-ab41-e8054a37492a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title hd1 Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=9ba02aa3-0349-4df3-ab41-e8054a37492a ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=9ba02aa3-0349-4df3-ab41-e8054a37492a ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=9ba02aa3-0349-4df3-ab41-e8054a37492a ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

