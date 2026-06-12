---
title: "How do I edit Grub?"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by katy98 on 2006-10-18
I have a dual boot with Linux Ubuntu and XP.  The Grub boot manager has linux being the primary boot and I'd like to change it to show XP primary.  Would it help to post my grub file to show what I have and where I can make changes?  I apologize for having to ask how to edit this as it might be misconstrued as preferring a different OS but I've been told that the Grub bootmanager needs to be editted vs. just going into a setting within the OS (where I could sneak in and do it without anyone knowing) to make this change and I know of no other way.  Could someone help me?](*,)   

I did get a reply in linuxquestion.org but the instructions to change did not match my grub file & he did recommend I contact this forum.  Could I post my grub file here for you to look at and tell me what to change, without exposing something critical?  I did also hear from the LQ.org reply that I would need to do this after each update so I do understand that.  I did check email notification, that's a super feature!  

I've heard nothing but great things about the Ubuntu forums, and any linux forum for that matter. :)   TIA for your help!! katy

---

### Post by moore.bryan on 2006-10-18
[I]i'm not sure i understand what you need...

do you want to have windows as the default os boot?

if so, just
```
sudo gedit /boot/grub/menu.lst
```
into a terminal, scroll down to the bottom where your os's are listed and put windows first in the list... that'll auto-load that.  there are a couple of other ways to do it, but that's pretty much the simplest.
[/I]

---

### Post by dbd on 2006-10-18
You can put menu.1st here with no probs, or just follow these insructions:


Near the top of menu.1st there will be a line which is probably:
default 0
This means that the default OS to boot is the first one in the list (computers like to count beginning with 0). So just count which number in the list of windows is, and then change the default number to that -1. (Because it counts starting with 0, if windows is 3rd in the list you want default to be 2).

An alternative solution is to move the windows section of menu.1st to the top of the bootloaders, so that it is first in the list, so if default is 0 then it will select windows.

By the way, to edit menu.1st you need root permissions, so on the command line window go to the menu.1st directory and open it with the sudo command, followed by the name of your text editor, followed by the file name, so to open with kdedit I would use:
sudo kedit menu.1st

Good luck

---

### Post by katy98 on 2006-10-18
> **moore.bryan said:**
> [I]i'm not sure i understand what you need...

do you want to have windows as the default os boot?

if so, just
```
sudo gedit /boot/grub/menu.lst
```
into a terminal, scroll down to the bottom where your os's are listed and put windows first in the list... that'll auto-load that.  there are a couple of other ways to do it, but that's pretty much the simplest.
[/I]

That's the hard part, I don't see where the OS's are listed.  I was told about the command you quoted: sudo etc. and the file was exposed but I did not see where the 2 OS's were listed, linux unbuntu and XP.  I did find a 'default 0' and I was told to change the 0 to the # given the XP or Other Operating System but I cannot find anywhere in the Grub file what # the Other Operating System was given.  

In the initial bootup, there is Ubuntu showing up several lines, for each update I assume and at the bottom is Other Operating System.  But the Grub file doesn't show a # for Other Operating System or for any of the other ubuntu updates for that matter.  Is there a way to show the Grub file here for you to point to 'the line'?  I tried viewing in notepad but it's all scrambled.  Is there another way?

---

### Post by louieb on 2006-10-18
What moore.bryan said will work until you do a kernel update. (then it will disappear) Follow his advise except find the line that reads:
```
### BEGIN AUTOMAGIC KERNELS LIST
```
and place your windows entry just before that line.

---

### Post by StormNet on 2006-10-18
Like dbd said, just adjust the default boot number, as an example i have included a cropped down version of the menu.lst file:

> default         4
timeout         10

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (single-user mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows Server 2003
root            (hd0,0)
savedefault
makeactive
chainloader     +1In this example, the first line would make grub boot into Windows Server since it is the 5th option in the grub menu (counting from 0 as dbd said.)

---

### Post by Tomosaur on 2006-10-18
Try the link in my sig, it may help you out :)

---

### Post by katy98 on 2006-10-18
> **dbd said:**
> You can put menu.1st here with no probs, or just follow these insructions:


Near the top of menu.1st there will be a line which is probably:
default 0
This means that the default OS to boot is the first one in the list (computers like to count beginning with 0). So just count which number in the list of windows is, and then change the default number to that -1. (Because it counts starting with 0, if windows is 3rd in the list you want default to be 2).  [COLOR="Red"]I changed the # to -1 and grub booted up exactly the same way as before I made the change. [/COLOR]
[COLOR="Red"]I guess I'd prefer to try one thing at a time, so I am hoping I am attaching the grub file (not sure how but will look & try).[/COLOR]

An alternative solution is to move the windows section of menu.1st to the top of the bootloaders, so that it is first in the list, so if default is 0 then it will select windows.

By the way, to edit menu.1st you need root permissions, so on the command line window go to the menu.1st directory and open it with the sudo command, followed by the name of your text editor, followed by the file name, so to open with kdedit I would use:
sudo kedit menu.1st   [COLOR="Red"]When I typed in the sudo command, I was asked for password so I guess that is the permissions thing [/COLOR]  [COLOR="Red"]Ugh! I tried uploading my menu.lst file from my USB drive where I save it and the forum reported 'upload errors' both from the USB drive and after dragging it to desktop and trying to upload from Desktop... that's about it.  [/COLOR]

Good luck
Now my message alert here says it's too short so am typing this....

---

### Post by StormNet on 2006-10-18
If you want to post your menu.lst file, just copy and paste the contents file into the reply section.
> gedit /boot/grub/menu.lst
That will allow you to select and copy the contents, but it will not allow you to change the contents of the file.

---

### Post by katy98 on 2006-10-18
My menu.lst file (this was before I changed the default 0 to -1:


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
default		-1

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
# kopt=root=/dev/sda3 ro

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

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by katy98 on 2006-10-18
Oh I think I know what happened!!  I saved to USB drive, then desktop but not to Grub (Duh!)  Now I saved to Grub and will reboot; brb

---

### Post by StormNet on 2006-10-18
If you want XP to be the default OS you can change the default to:
> default 6That will make XP the default OS.

---

### Post by katy98 on 2006-10-18
Not sure where my other quick reply went but :) I saved the menu.lst to grub and rebooted but boot looked exactly the same, even with the default -1.  Did I change the wrong line?

---

### Post by katy98 on 2006-10-18
Wonderful!!  Line 6 did the trick!  Thanks Storm and all who responded!  This is the best forum I'm been in in a very long time!!!  Thanks everyone for all your help and I think I now understand the grub file more also.  now with each update, I would need to adjust the grub file for the new line the other OS is on if I care to change it.  But if I don't want to change it, I can move it back to default 0.  Or I can try louieb's advise about the line 
[COLOR="Blue"]### BEGIN AUTOMAGIC KERNELS LIST 
and place your windows entry just before that line.[/COLOR]
This sounds really sweet and might be my saving grace. Thanks again ALL!!!!!!

---

