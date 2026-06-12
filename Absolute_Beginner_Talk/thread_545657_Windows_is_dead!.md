---
title: "Windows is dead!"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by federicotedin on 2007-09-07
Hi, 

Today i was using Windows, I rebooted, use Ubuntu, rebooted again and when o tried to start windows XP i get a black screen (NO TEXT) and XP never starts up.  Heres a copy of my grub.lst:

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
# kopt=root=UUID=4589a731-e256-4eec-b660-69dd0f63e1e2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4589a731-e256-4eec-b660-69dd0f63e1e2 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4589a731-e256-4eec-b660-69dd0f63e1e2 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4589a731-e256-4eec-b660-69dd0f63e1e2 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4589a731-e256-4eec-b660-69dd0f63e1e2 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

it is strange as Windows worked today

---

### Post by federicotedin on 2007-09-07
PLEASE help!!!
The Windows CD doesn't start up either!!
i cant acces windows!!
i have reinstalled ubuntu and grub but it still doeasnt work, what can i do?
please help i have important files there!
thanks

---

### Post by nicenick on 2007-09-07
I learned how to get Ubuntu to mount an NTFS partition/drive, (I don't rememer the command line now, but it can be found easily in the ubuntu forums). I know I used gparted to find the NTFS partition so I could use that information to mount the NTFS partition. I recovered all my windows files, then promptly reformatted the ntfs partition t o ext3 and never looked back. To date I can find NOTHING I can do on my 'at work' windows computer that I can not port into and out of my 'Home Ubuntu' computer.  Open Office is AWESOME compared to MS Office.  I simply tell my Open Office to save documents, spreadsheets, power-point presentations in Microsoft compatible formats and then all my work appears on my 'at work' windows computers (98 and Xp) without a hitch.

Sorry I could not be more helpful, but I dumped windows when I couldn't boot XP after I replaced a damaged  motherboard in an HP pavillion computer without begging HP to please activate my Xp for only an addition $75.00 plus shipping and handling.

Regards,

Nice Nick

---

### Post by thelocust on 2007-09-07
**"Windows is dead!"**

Damn it you got me excited

---

### Post by pinoyskull on 2007-09-07
boot to your Ubuntu, identify the partition of your winxp by running this command on terminal
```
sudo fdisk -l
```the filesystem with HPFS/NTFS on it is your winxp partition, mount that
example. 
```
mount -t ntfs-3g /dev/sda1 /media/disk
```

after your winxp is mounted, backup your data then reinstall winxp :)

---

### Post by federicotedin on 2007-09-07
Thanks, but the problem is that i have a vouple of programs that only work on Windows and not in WINE, and besides Ubuntu has made my HDD uselelss, now i can-t boot from the Windows CD.  I like Ubuntu but it has totally deleted all the Windows part of my PC, and i would like to have back what i paid for withput having to reisntall, whcih i can-t becouse the XP CD doesn-t even start up, i dont know why, it did before Ubuntu 
HELP

---

### Post by pinoyskull on 2007-09-07
Ubuntu deleting Windows? That's new :)

I'm sure it's not your Ubuntu that killed your Windows, that is unlikely, it could be that your Windows install is corrupted or was inftected with a virus.

---

### Post by federicotedin on 2007-09-07
Thanks for the suggestions,
sorry i cant use any apostrophies and parenthesys im using ubuntu from the LIVEcd
but i dont know what to do next.  There are people in this house who need windows.  Windows worked today, perfectly.  I used Ubuntu, then ttried to use Windows and it stuck in a black screen.  Maybe it-s a virus, but i dont think so, as it worked perfectly today.  What is VERY strange is that the Windows XP CD doesn-t start.  I just doesnt.  It worked perfectly before Ubuntu,  Ubuntu has done something to my HD and now im stuck.  Any ideasPLEASE
THANKS HELP THANKS PLEASE

---

### Post by ORBiTrus on 2007-09-07
> **pinoyskull said:**
> Ubuntu deleting Windows? That's new :)

I'm sure it's not your Ubuntu that killed your Windows, that is unlikely, it could be that your Windows install is corrupted or was inftected with a virus.

No, that's not new.  It's old.  Bugs worked out in alpha, in fact.

Seriously though, doesn't ANYONE pay attention to the warning to back up your data, that an operation is being performed which if it goes wrong will fubar the machine?

Still, IF THE PARTITION IS STILL LISTED IN THE TABLE, it is recoverable.  If Ubuntu overwrote Windows (which you would have to manually tell it too), then you are SOL.  Sorry.

Edit: For the record, in the past Linux has had trouble with partitions not on cylinder boundaries.  The recovery path I would suggest involves running to the store, buying Partition Magic and a spare hard drive, installing Windows on the space, wire it up as primary-master, then use Partition Magic to copy over the original Windows partition onto the new drive.  Or, take it to some pros who (IF they are worth their salt) could do all that pretty quickly - maybe half an hour of actual work, and 2 hours of thumb-twiddling)

---

### Post by Snoopyowns on 2007-09-07
It sounds like either Grub is having trouble loading up Windows, or the Windows installation is corrupt. You probably want to make sure your bios is set to boot from CD-ROM, put in the Windows CD. Choose to repair the installation and do a fixmbr. 

Another thing you may want to do while you have the LiveCD open is to browse to the Windows HD and verify that there are still files on that drive.

---

### Post by irish_flu on 2007-09-08
As far as starting the Windows CD, go into your BIOS (may be called "setup") right after your computer boots and make sure your CD ROM is set as a boot device *before* your hard drive.  Then, with the XP CD in the drive, reboot the computer.

See, no matter what Ubuntu (or Windows, or anything) "did to your hard drive", it doesn't stop you from booting to a CD.

I'm curious as to why you're sure it's Ubuntu's fault; Windows (just like Linux) can fail just fine on its own.

Did you notice anything odd or different before this happened, or did you do anything differently than what you'd normally do?

---

### Post by pinoyskull on 2007-09-08
**ORBiTus**
new to me cuz I haven't experienced something like that before, but anyway thanks for the correction.

---

### Post by federicotedin on 2007-09-08
The problem is that the Windows XP CD doesnt work.  I tried it with another computer and it worked perfectly, but with this one i only reach the first stage were it says configuring blahblah in white letters, and then it just stucks in a black screen.  I checked the NTFS partition and i see everything all right.

THIS MAY SOUND STUPID> in the C drive, the folder WINDOWS doesnt show up... maybe its normal...can you see the folder from your Ubuntu out-of-the-Box, no additional NTFS reader -writers included?

IF THE WINDOWS FOLDER ISNT THERE... then>
Why doesn-t the XP CD start in this PC?
How was I using windows without a Windows folder?

COULD you guys check if Ubuntu detects the WINDOWS folder? thanks!
also... can u answer my questions? (if my WINDOWS folder was deleted somehow)
I hope my WINDOWS folder still exists...
thanks!

---

### Post by ORBiTrus on 2007-09-08
> **pinoyskull said:**
> **ORBiTus**
new to me cuz I haven't experienced something like that before, but anyway thanks for the correction.

God I hate it when people correct me.  I hate it even more when people thank me for correcting them.  You are supposed to curse me.

-----------

frederico, disconnect your hard drive.  Does the CD still fail to load?

Second, do you have retail, OEM, or manufacturer supplied?  The first two should work, but manufacturer can be issues.

---

### Post by Snoopyowns on 2007-09-08
Yeah, I can see the Windows folder while in Ubuntu.

---

### Post by federicotedin on 2007-09-08
Is there a way to disconnect the hard drive without having to unplug it?

Also, what I dont understand is:

Why doesn't the Windows CD start anymore?
Why Windows doesn't work anymore after being used in the same day?
How are they both connected? (if they are)
What can I do? Im stuck here, my PC no longer 'reads' the Windows CD... and there are people in my house who need Windows...
If the Windows CD worked (it actually does i tried it with other PC's) in this PC could i fix this?

Help!!
(thanks you guys for all the help given until now!!)
thanks for helping me out of an uncomfortable situation

---

### Post by Snoopyowns on 2007-09-08
> **federicotedin said:**
> Is there a way to disconnect the hard drive without having to unplug it?

You can disable it in the Bios. Will do the same thing pretty much. Instead of using "Auto" or a set type, choose "None", or at least thats the term thats typically used in most Bios'.

---

### Post by ORBiTrus on 2007-09-08
> **Snoopyowns said:**
> You can disable it in the Bios. Will do the same thing pretty much. Instead of using "Auto" or a set type, choose "None", or at least thats the term thats typically used in most Bios'.

This is a warning for anyone else who reads this thread:

Don't do this if you have an older PC.  You MAY, on certain older (<400MHz era) models be UNABLE to autodetect the correct settings, and have to manually find out the cylinders/sectors/heads values from the spec sheet written on the hard drive itself. It's a pain.

---

### Post by federicotedin on 2007-09-08
i did that already.. deactivated the HD from the BIOS.. but the CD still doesn't work on THIS PC

---

### Post by Snoopyowns on 2007-09-08
> **ORBiTrus said:**
> This is a warning for anyone else who reads this thread:

Don't do this if you have an older PC.  You MAY, on certain older (<400MHz era) models be UNABLE to autodetect the correct settings, and have to manually find out the cylinders/sectors/heads values from the spec sheet written on the hard drive itself. It's a pain.

Or... write it down first :P

As for the Windows CD problem with it freezing during the initial loading, I've seen that mentioned other places in these forums. I'll do a bit of searching to see what comes up, but you may want to search around a bit yourself.

---

### Post by Baarhisveiki on 2007-09-08
Besides not being able to boot your Windows. Their are some windows apps i need to keep on using just like you.

I just use innotek Virtualbox on my linux partition which "virtual" runs windows and it works like a charm for me. off course it does not support 3d so for instance newer games are out of the question.

I only use it for my glucose reader (diabetic and no linux app supports my meter) and some other apps that run unstable with the wine emulator on linux. 

Its just a tip. But then again if your installation cd of windows is corrupted (as some posts here suggest) it is unlikely to run in a Virtual box....and the box need some configuring to do but it works for me.

---

### Post by ORBiTrus on 2007-09-08
> **Snoopyowns said:**
> Or... write it down first :P

As for the Windows CD problem with it freezing during the initial loading, I've seen that mentioned other places in these forums. I'll do a bit of searching to see what comes up, but you may want to search around a bit yourself.

What's this, a suggestion that a Linux user actually have paper near them?  Pens and pencils aplenty abound around the able engineer, absolutely.  But by what perchange would place a proper protocol such as providing plenty of paper at present that some point about planning need not be pushed?

OK, that wore me out.  Good Night and Good Luck.

---

