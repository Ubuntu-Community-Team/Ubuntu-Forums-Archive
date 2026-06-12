---
title: "Dual boot 2 HDD XP and Ubuntu"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by LA TRIPP on 2007-08-03
Ok, here's what I've got and what I'm trying to achieve.  Any help is appreciated.  

I've got two 60G HD's, one with XP and one with Ubuntu.  I am dual booting.  I want the Ubuntu to be Master and have the drives set up that way.  I have no problem booting into Ubuntu.  I can hit escape to show the menu options to get to XP.  I'd rather dual boot with both choices directly on the screen w/o using escape, but if that's not possible, this way is fine.   Both HD's are IDE.   

So anyway, when i try to boot into XP it usually will not fully boot the first time around.  I have to shut down (hold power button) and boot back up to fully get into XP.  I want a smooth boot into either OS.

Here is my menu.lst:

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
# kopt=root=UUID=54dbc31d-288e-48bc-b92a-8a16286b9dfc ro

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=54dbc31d-288e-48bc-b92a-8a16286b9dfc ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=54dbc31d-288e-48bc-b92a-8a16286b9dfc ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title WindowsNT/2000/XP (loader)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

Is that where my problem is?

---

### Post by Doberman92 on 2007-08-03
It sound to me like you installed Ubuntu first (hard drive #1) and Windows XP second (hard drive #2). If I am correct, then Windows has overwritten the Master Boot Record. When you press escape, you are using Window's OS select option. You should reinstall GRUB. This link should tell you how to reinstall it correctly, then once that is done it will automatically boot to Ubuntu first (unless you edit the menu.lst file). As for Windows not booting correctly, I believe that is an issue with Windows having a preference to be on the first hard drive. Once you install GRUB, it should be fine.

[HTML]http://ubuntuforums.org/showthread.php?t=2243151[/HTML]

Just a word of caution: screwing this up will cause much pain. If you hit any snags, come back here and we will try to help you.

---

### Post by LA TRIPP on 2007-08-03
Actually, I installed them seperately.  In other words, I did one HD at a time, then put them both in together.  Ok, let me back up.  Windows was already on the HD that was in the computer, then I put Ubuntu on the other one, while XP was out.  Then I put them both in together.

---

### Post by Doberman92 on 2007-08-03
Then I would suggest to still reinstall GRUB and see what happens.

---

### Post by shane2peru on 2007-08-03
If you can boot into Ubuntu then grub is fine the way it is.  If you want to not have to hit escape to select see your menu then in your menu.lst you need to comment out this line: ```

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

``` 
by making it look like this:

```

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

```

That should make your menu visible on boot up.  If XP is not booting sometimes and is other times, That sounds like a harddrive issue that perhaps the drive is going bad, or your installation has problems.  

Shane

---

### Post by Doberman92 on 2007-08-03
shane2peru,

Does Ubuntu usually install GRUB with the hiddenmenu part automatically in menu.lst? Mine didn't for some odd reason. I figured that since his XP drive wasn't in the computer at the time of the Ubuntu installation, GRUB might not recognize it correctly. Me and my silly theories.

---

### Post by LA TRIPP on 2007-08-04
Thanks to both of you for your suggestions.  I'm guessing that since no one has said the GRUB I posted is wrong, that that's not the problem?  I was wondering about the mapping of the hard drives.  

Well, as far as the hard drive going out . . . obviously I hope not.  As far as the installation, I bought the computer used and XP was already installed on it, so I didn't install that OS on that computer.  

All I did was take another HD I had and put it in there solo and install Ubuntu then made that one the master and switched the jumper on the XP for slave and put them both in there.

I'd rather have Ubuntu be the master, but would both OS's boot smoother if I just gave in to MS?

---

### Post by shane2peru on 2007-08-04
> **Doberman92 said:**
> shane2peru,

Does Ubuntu usually install GRUB with the hiddenmenu part automatically in menu.lst? Mine didn't for some odd reason. I figured that since his XP drive wasn't in the computer at the time of the Ubuntu installation, GRUB might not recognize it correctly. Me and my silly theories.

I believe it does, I know it does when it is the only operating system detected.  However when it is installed in a dual-boot environment, I don't think it does, but I could be wrong on that.

> **LA TRIPP said:**
> Thanks to both of you for your suggestions.  I'm guessing that since no one has said the GRUB I posted is wrong, that that's not the problem?  I was wondering about the mapping of the hard drives.  

Well, as far as the hard drive going out . . . obviously I hope not.  As far as the installation, I bought the computer used and XP was already installed on it, so I didn't install that OS on that computer.  

All I did was take another HD I had and put it in there solo and install Ubuntu then made that one the master and switched the jumper on the XP for slave and put them both in there.

I'd rather have Ubuntu be the master, but would both OS's boot smoother if I just gave in to MS?

You should be able to boot fine with the setup the way it is, if it boots sometimes and doesn't others, I would say that is a hardware failure.  The best way to check it is to change the XP drive back to master and plug it in as master and boot off of it about 2 or 3 times to make sure it is working fine, if it does, then you have a problem with your mapping.  I don't know much about mapping the drives though, so I can't be of much use to you.  I do know that there is a little part on the hdd and when it burns up, XP doesn't like to use it, however the drive is not necessarily bad, just XP won't use it.  Although I don't know how long it may last after that.  I have been there done that with XP and got the t-shirt.  :)  And continue to use the drive as a secondary drive on Ubuntu for non critical files.

Shane

---

