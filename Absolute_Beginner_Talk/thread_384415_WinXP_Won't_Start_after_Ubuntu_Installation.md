---
title: "WinXP Won't Start after Ubuntu Installation"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by dajayhawk on 2007-03-14
I just installed Ubuntu edgy on my relatively new Compaq Desktop Computer.  I do not know much about Ubuntu.  I installed it and it seems to be working must fine.  However, If i click Windows xp to start at the OS select screen when the computer starts.  It goes to an all black screen and only says "starting up ..."  It never starts.

Pleaz help me!!!!

---

### Post by undertherift on 2007-03-14
Is grub installed correctly?  Can you describe your partition scheme a little more?  I'd like to see your menu.lst and the output of fdisk -l ... just to identify that grub is loading the right thing.  Sorry if its rudimentary.

I'm asking beause i've never seen grub (or windows xp) show a 'starting up...' message.  Or do you mean that screen where the bar is loading winxp, with the logo?  Can you clarify some?

---

### Post by dajayhawk on 2007-03-15
It shows an all black screen with the white letters saying at the top left corner "starting up ..."  It never gets to the point where it has the Winxp startup screen with the bar.
When I partitioned it i just let ubuntu do it automatically at the setting it already had.  There was some bar that I slid and i put it at around 66% i think.  I have no idea if grub is installed correctly or not.  I did not do anything with it.  

I'll try and post menu.lst and the output of fdisk -l.  However, I dont understand why an application called grub on ubuntu would make a difference as to whether winxp would start or not.

Thanks for the help!  sorry if i seem really dumb

---

### Post by undertherift on 2007-03-15
No, of course you don't sound dumb.  Just sound like someone who hasn't done this yet - which is totally acceptable because we were all there at some point in time. :) I'm not an expert, but i'll try my best here.

Grub is a bootloader.  It writes over the master boot record on your hard drive.  SO, when you start up your computer, grub starts up, giving you the option of booting to XP or Ubuntu.  You can think of Grub as an independent "application" - it runs independently of both linux and windows.  It should have installed properly, and sounds like it did if you're not getting a grub error.

So, just as a brief overview of what i think we oughta do... 
1. boot back into ubuntu
2. look at the menu.lst file (this is the file that tells grub what to do)
3. get the output of fdisk -l (this tells what your hard drive setup looks like)
4. mount your windows partition, and make sure windows is still there.

I am afraid that you may have blown away your windows install, depending on how you let ubuntu install.  Do you have a spare computer around?  I want to make sure (before trying anything drastic) that you're not going to lose all methods of communications. And do you have a winxp install cd around?  Eventually, we may just need to wipe out grub (run a command from the recovery console on the windows cd), and then reinstall it.

---

### Post by dajayhawk on 2007-03-15
alright 
i'll post all that stuff tomarrow morning
how do i "4. mount your windows partition, and make sure windows is still there."
thanx

---

### Post by undertherift on 2007-03-15
Don't know where you are, so tomorrow morning doesn't mean too much to me (except 8 hours from now). 

You're going to need the output of fdisk to know what device you're trying to mount. This guide will tell you how to do almost anything you need to do in ubuntu - great place to start, and they have one for each version. Let me know how it goes. 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows)

---

### Post by dajayhawk on 2007-03-21
Here is my menu.lst

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
# kopt=root=UUID=8183be8b-24fc-4a74-a002-4b04d866bc52 ro
# kopt_2_6=root=/dev/sda3 ro

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1


I'm not sure how to find the output of disk -l

---

### Post by rusty4r on 2007-03-21
Just a note, grub thinks you have two windows operating systems. Do you?

You said "relatively new Compaq" which means to me that windows came preinstalled and what you have is a recovery disc. Is that right?

If so, Compaq usually puts a "D:/ drive" partition on your hard drive to store your backup windows files that the recovery disc will use to do its recovery.

Does this sound like what you have?

---

### Post by undertherift on 2007-03-21
Ok, we're going to have to get a little messy in the command line, cause that's the best way i know how to do this. We're going to open up a terminal, get an output of your disk structure, and mount your windows partitions so you can see them in ubuntu. 

I was going to post just now, but then i realized i don't want to make a mistake (i dont have a linux machine here), so i'll have to wait until i get home from work (~ 7 hrs from now). 

In the meantime: assuming you're using standard ubuntu (ubuntu with gnome), go to Applications, then Accessories, and click on Terminal.  It'll give you a nice little message about ubuntu, and then take you to a command line.  This is the Command Line Interface (CLI), and the thing that people are afraid of (don't worry, you'll be fine). 

This is what you type:

```
vik@ubuntu:~> fdisk -l 
Disk /dev/hda: 429.4 GB, 429496729600 bytes
255 heads, 63 sectors/track, 52216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

 Device   Boot    Start       End        Blocks   Id  System
/dev/hda1        1     52216 419425019+  83         Linux
```

This is telling me that i have a linux partition as my only partition on my 430gb system. Grub thinks you have multiple disks (its probably right), and multiple operating systems. 

It will spit out a response.  Copy that and Paste it back here.  We'll use this as the brick for mounting your windows drives. Oh, and try to use the code tags a the top of this editor window - it makes things easier to look at.

---

### Post by dajayhawk on 2007-03-21
i'm not on my home ubuntu computer right now either

do u think i'll need the windows disc? cuz i dont have it

i do have a recovery mode for windows and it works just fine.

---

### Post by dajayhawk on 2007-03-21
wait.  that code you just gave me there, that is what you want me to type in the terminal or...?

i dont have a 430gb system, what r u talking about

what in simple terms did i do to mess up my system?

thank you

ps sorry again for sounding like a complete dumbass as i'm sure i do

---

### Post by undertherift on 2007-03-21
Sorry - what do you mean a recovery mode?  

When you select Windows Media Cetner Edition from Grub, what happens? 

What happens when you select Windows NT/2000/XP ?

Here's my theory:  Grub saw your recovery partition, and regular windows partition, and listed each of them seperately.
I didn't realize you might have a recovery partition - thanks Rusty4r for pointing that out.

---

### Post by undertherift on 2007-03-21
No, thats just the example of my out put from 'fdisk -l'.  
You go into the command line, and type 'fdisk -l', and it will output the information against your system. 

As far as messing up your system, i'm fairly certain you didn't do anything.

---

### Post by dajayhawk on 2007-03-21
ya
there is one option that is windows media center edition and when i click on that it goes to the all black screen and says starting up ... 
if i click on windwows nt/2000/xp, it works just fine but its some weird recovery thing.  it appears to work as it shoudl though.

---

### Post by rusty4r on 2007-03-21
I'm not so sure that the recovery partition will still be recognized by the recovery disk. I tried to copy a recovery partition once in order to upgrade the size of my harddrive and the new drive did not ever let me use recovery disc anymore.

---

### Post by undertherift on 2007-03-21
Rusty - isn't he booting to the recovery partition now though?  (when he selects NT/2000/XP)

Couldn't he just recover it, then reload grub?  Sry, i don't know how the recovery partition is supposed to work, reading up on it now.

EDIT:  As i read it, you've got 4 options
> Restore option   	 Description
**Emergency Diskette **	Creating this diskette is important as it allows you to save your computer's unique setup information for use in the event of an                                        emergency. Store the diskette in a safe place.
**User Backup 	**            Backs up all information and files on your hard drive and stores them in a separate partition on your drive.
**User Restore 	**            Restores your hard drive to the state it was in when you last used User Backup.
**Factory Restore 	**   Restores your computer to its original factory-installed software state.

All of these claim to edit/restore the hd to previous state - does that mean that they'll reformat/change partition structure (even in User Restore)?

---

### Post by rusty4r on 2007-03-21
Thats what I gathered too. But I'm not sure how his recovery program works. My recovery partition was compressed and would never have booted, ao now I am confused and can't wait to see his fdisk-l and am curious about both being bootable or is the first one his recovery partition, probably not. According to his other post he may not have internet running yet at home until he gets one of them running, is that correct dayjayhawk?

---

### Post by wog on 2007-03-21
I seem to remember there was an incompatibility between XP and Linux that was fixed with service pack 2. Before sp2 the only thing that would come up would be linux, although linux would see the partition windows was in.

Unfortunately, this is all second-hand info, and I haven't tried a dual-boot machine since then.

I'm betting the Recovery Mode would wipe out grub and repair the boot to Windows as the default. Windows isn't very friendly toward dual booting. This probably means reformat, but not necessarily repartitioning the drive.

---

### Post by mangoti on 2007-03-21
> ya
there is one option that is windows media center edition and when i click on that it goes to the all black screen and says starting up ... 
if i click on windwows nt/2000/xp, it works just fine but its some weird recovery thing. it appears to work as it shoudl though.

My guess here is that dajayhawk tried to boot both windows listed by grub. The "Windows NT/2000/XP" option (which is shown when grub doesnt recognize it as XP) being the recovery partition, lauching it means that it made some changes to the XP installation which can include formatting and putting some startup files on the C: drive; that would explain the "starting up..." message. The restore process might have been interrupted before C: is fully restored, preventing the system to boot properly.

Solution? I dont know the extent of the dammage, but it can go as far as wiped out C: partition. I would make an image of it and try some disaster recovery procedure.

---

### Post by dajayhawk on 2007-03-24
ya
i just went through with the recovery thing
it worked fine
then i reinstalled ubuntu and it somehow works fine now

thanx for all the help

---

