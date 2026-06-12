---
title: "Dualboot problem with SATA HD and IDE HD"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by Kleaefmiir on 2007-04-13
Hello!

I've been installing Ubuntu 7 times now without success... my computer is going to get mad at me if this continues (from all the install and formating).

Ok, here is situation:

I got a PC dual core 3.4GHz each, motherboard is P5LD2, got a 200Go SATA plug on the first SATA port on the motherboard and a 80Go IDE plugged onto the primary IDE port on the motherboard. The IDE drive has no jumper on it (master or single setting).
I updated my bios to latest version to make sure all is good.
The SATA HD is set to boot before the IDE HD (When i built my computer last summer i set it that way, but i dont remember how and where in the BIOS to change it... anyone knows?!).

Ok, so here is the problem:

I install Windows XP on a 40Go NTFS primary partition on the 200Go SATA (for some obscure reasons, the IDE HD is not detected in the Windows XP installation, but it is detected once the install is complete and log in Windows) (In the Linux install, it is mounted as /windows). I got Linux on a 158Go EXT3 extended partition and the remaining 2Go as the SWAP partition (extended as well). The IDE HD, i tried to put the /home (or a /telechargement [french for /download] to test if the /home was the problem in the install) on it, EXT3 primary partition.
All seemed good to me at that point since the installer was not bugging me warnings (it did when i forgot to mount my IDE HD and the windows Partition).
So i proceeded with the intallation until the end, no problem. But when i reboot, after the installation is finished, all i get is Windows to boot. No GRUB menu to select the OS I want to boot into...

I also tried to install Linux on the 200Go SATA as described above but without Windows XP (so Linux uses all the 200Go), but again when i boot there is a problem: "Erreur lors du chargement du systeme d'exploitation" ["Error while loading the operating system"].

Here is a few things I've noticed:
When i finish setting up my partitions, it says GRUB will be installed (hd0). I am wondering if this means Linux thinks my 1st HD is the IDE and install the GRUB on it? Wouldnt it be (sd0) for SATA drive (i tried it but i get an error during the install, not being able to install it. I also tried (sda) just in case it would work, but it gives me an error in the installation as well.)?

What do I have to do?:confused: 
I want to run one of these scenarios:
1)
SATA = 40Go Windows XP + 158Go Linux + 2Go SWAP
IDE = 80Go Linux /home (or a /place-to-store-random-things)
2)
SATA = 40Go Linux + 158Go Linux /home + 2Go SWAP
IDE = 80Go Windows XP

The problem in #1 is that Linux GRUB seems to be installing somewhere else rather than on the MBR of my SATA HD.
The problem in #2 is that Windows XP can't find the IDE HD during it's installation (probably something to do with my BIOS configuration that is wrong in the HDD priorities and boot sequences) while I think Linux does, in fact, install the GRUB on the MBR of the IDE drive.

In both cases i got 1 problem to solve i dont know how.

Anyone skilled enough to sort this out and help me? It would be much appreciated since I'd like to have fun with Ubuntu too (while keeping Windows XP for my girlfriend and some games).

N.B.: I tried Ubuntu 6.10 and 7.04, same problem occurs.

Thank you very much in advance!

---

### Post by izizzle on 2007-04-13
hello,

i believe i am understanding your dual- boot problem. I think that it is a problem with your harddrive rather than the OS. try backing up your info and formatting the harddrive(s) on you computer. than reinstall ubuntu first, then windows.

Hope this helps,

Imran

---

### Post by Scunizi on 2007-04-13
6.10 & 7.04 use a different drive discovery feature.  I'm using dapper and had issues with a mix of sata and ide.  Being new, what I did was to disconnect my ide and install xp on sata.. with everything working there I kept the ide disconnected and installed Dapper 6.06.  Even though I don't have raid activated in the bios I had to follow the release notes to deactivate raid.  After all this everything worked great.  I added my ide back in and manually reconfigured fstab and I had a full system again.  Later I discovered that on my original install grub had been put on the ide instead of the sata.  To fix this situation follow the guide at [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm).  It worked very well for me and may just fix your issue without having to reinstall yet again.

On my scenario, if you go that route, you will be able to move home to the ide.  I know it's possible I just don't know how.

---

### Post by Scunizi on 2007-04-13
Note:  Installing ubuntu first then windows will create another situation where windows will overwrite your grub and you'll have to fix it yet again.

---

### Post by Kleaefmiir on 2007-04-13
I have formatted my HDDs countless of times in all my tries to install WinXP/Linux.

I will got check that site out... hope it works.

If anyone got more suggestion, I'll take them! :D
Keep them coming!

Thanks for the quick replies.

---

### Post by Kleaefmiir on 2007-04-13
> **Scunizi said:**
> 6.10 & 7.04 use a different drive discovery feature.  I'm using dapper and had issues with a mix of sata and ide.  Being new, what I did was to disconnect my ide and install xp on sata.. with everything working there I kept the ide disconnected and installed Dapper 6.06.  Even though I don't have raid activated in the bios I had to follow the release notes to deactivate raid.  After all this everything worked great.  I added my ide back in and manually reconfigured fstab and I had a full system again.  Later I discovered that on my original install grub had been put on the ide instead of the sata.  To fix this situation follow the guide at [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm).  It worked very well for me and may just fix your issue without having to reinstall yet again.

On my scenario, if you go that route, you will be able to move home to the ide.  I know it's possible I just don't know how.

It seems to have some info on my problem on that site, thanks!
I'm reading it at the moment and will try the solution. I'll keep you updated on the results! :D

---

### Post by Kleaefmiir on 2007-04-14
I tried changing the device.map then reboot.

I could get to Grub, but when I picked Ubuntu i got error 22!!
Same with Windows, it couldnt load from Grub.

At least I got some progress to load Grub, what should I do to correct the error 22?

N.B.: I restored Windows MBR to be able to come here. How to i set Grub back on? I tried Herman tutorial, but it seems i missed something cause it didnt worked... step by step please. thanks!

Thank you for helping!

(10th Ubuntu up to now... lol Hope i wont have to reinstall again). :popcorn:

---

### Post by Kleaefmiir on 2007-04-14
Yay! I got it fixed up!

Here is what I did:
I opened my /boot/grub/device.map and changed the drive to set my SATA as hd0 and my IDE as hd1 (it was the other way around).

Then, i opened the /boot/grub/menu.lst and changed every hd1 pointed to my SATA to hd0.
Here is what it looks like now:
> 
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
# kopt=root=UUID=1870c3ea-3b58-40d5-97fe-c0e0e4fcf4ba ro

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

title		Ubuntu, kernel 2.6.20-12-generic
root		(hd[COLOR="Red"]0[/COLOR],4)
kernel		/boot/vmlinuz-2.6.20-12-generic root=UUID=1870c3ea-3b58-40d5-97fe-c0e0e4fcf4ba ro quiet splash
initrd		/boot/initrd.img-2.6.20-12-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-12-generic (recovery mode)
root		(hd[COLOR="Red"]0[/COLOR],4)
kernel		/boot/vmlinuz-2.6.20-12-generic root=UUID=1870c3ea-3b58-40d5-97fe-c0e0e4fcf4ba ro single
initrd		/boot/initrd.img-2.6.20-12-generic

title		Ubuntu, memtest86+
root		(hd[COLOR="Red"]0[/COLOR],4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professionnel
root		(hd[COLOR="Red"]0[/COLOR],0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


That was really simple, I shouldnt have reseted my MBR with Windows'. I'll know when I reinstall! Cheers!

Thanks everyone for your support!

N.B.: It allowed me to learn a lot about bootloader! lol Doing all the research and stuff! :P

---

