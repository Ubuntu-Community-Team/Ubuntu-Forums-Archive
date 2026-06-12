---
title: "Unmountable_boot_volume"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by magnoliablossom on 2006-07-25
I've reformatted, partitioned, installed Windows, then Ubuntu several times and I always get the same results....Okay...This time I read the blue screen that comes up when I try to go back into Windows after I've installed Ubuntu.  It appears the problem Windows is having is that it's unable to mount the boot volume after Ubuntu installs (here's what it says):

A problem has been detected and Windows has been shut down to prevent damage to your computer.

UNMOUNTABLE_BOOT_VOLUME

If this is the first time you've seen this error blah, blah, blah....it goes on telling the normal stuff about booting into safe mode...

Any ideas how to fix this?

Here is also a copy of my grub menu.

[PHP]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

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
[/PHP]

Any help would be appreciated.

---

### Post by magnoliablossom on 2006-07-25
LMAO....sorry about the smilies in that post.

---

### Post by magnoliablossom on 2006-07-25
Okay...I give up...I would love to have it but obviously it's not going to work on my system and I'm tired of screwing with it.  Every time I install it, it's the same thing and it's two more hours of reformatting and reinstalling before I can get back to ask just one question for yet another thing that isn't going to work.  I figured that out by doing a search for "unmountable boot volume" and not a single one that had this problem was resolved.

---

### Post by catlett on 2006-07-25
If you make another try, do not have windows drive connected when you install ubuntu. That way windows drive will not have any chance to be "corrupted".
Do this. Once windows is back to normal, remove the drive. Put ubuntu in alone as the master. Run the installer and let Ubuntu install.
After the install is over, attatch window's drive as the SLAVE. Keep Ubuntu as the MASTER.
Now open grub's menu list to add an entry to boot windows from the slave drive.
```
sudo gedit /boot/grub/menu.lst
```
Then add this entry at the bottom for windows
```
title           Microsoft Windows 
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```
That entry will trick windows into thinking it is the first drive. It should mount with no problems because nothing on that drive was touched.

Just in case you wanted to try one more time.

---

### Post by magnoliablossom on 2006-07-25
can't do that.  i'm putting them on the same drive.

---

### Post by Sef on 2006-07-25
Have you checked out [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub")?

---

### Post by magnoliablossom on 2006-07-25
Haven't tried that.  But the menu is showing up fine.  it's just window's that's being a butt.  I don't mean to sound like an idiot but how is restoring something in Ubuntu going to fix what's wrong with Windows?

---

### Post by magnoliablossom on 2006-07-25
How do I change my menu to list windows first.  what exactly is it that i'm looking for and how do i go about changing it once i find it?

---

### Post by confused57 on 2006-07-25
You could try restoring your Windows mbr by booting up with the Windows installation CD, then press "r" for recovery mode, then enter **fixmbr**.  This should enable you to boot Windows.

You could then reinstall Dapper using the alternate CD, and when it asks where to install grub, select floppy...that way, insert the floppy when you want to boot Dapper.  Windows should boot up without the floppy inserted.

It may be a workaround for the time being, if you're still interested in dualbooting.

---

### Post by Sef on 2006-07-25
> I don't mean to sound like an idiot but how is restoring something in Ubuntu going to fix what's wrong with Windows?

1) You don't sound like an idiot.

2) Figured it was worth a try.

3) Possiblities

a) The hard disk has a bad sector.

solution: Run Scan disk.

b) XP is messed up.

Solution: Use a friend's XP to install and your auth number.

c) Ubuntu is messed up.

Solution: Download and burn another copy

---

### Post by magnoliablossom on 2006-07-25
tried the fixmbr and still had the problem.  i think it's a windows problem and not an ubuntu problem.  [http://support.microsoft.com/default.aspx?scid=kb;en-us;Q297185]("http://support.microsoft.com/default.aspx?scid=kb;en-us;Q297185")<--- i just replaced the cable but i'm not certain if that's the problem or not.  anyway, can you configure grub to boot from a cd?  i ain't got any floppies at the moment. lol

---

### Post by SkyNet2029 on 2006-07-26
This problem isn't really Grub related. Here is what 
Microsoft says about it; 


>  SYMPTOMS
When booting up to Win XP you may get a error that reads "Unmountable Boot Volume".

         CAUSE
  
Source: MS Knowledge Base Article number 555302.
 1.The file system is damaged and cannot be mounted.
 2.You use a standard 40-wire connector cable to connect the UDMA drive to the controller instead of the required 80-wire, 40-pin cable. 
 3.The basic input/output system (BIOS) settings are configured to force the faster UDMA modes

The other action that usually precedes this stop-error on an XPHome/Pro. is a large Windows Update. (Like installing Windows Service Pack two)

What you really need to repair the XP side of the house is to 
run the command 

'chkdsk /r'  ,
wthout the quotes from within an Recovery Console.

---

### Post by magnoliablossom on 2006-07-29
Well after 3 or 4 days of d/ling and installing Win XP service pack 2, I *FINALLY* got it to dual boot with no problems!  I guess I should have done that the first the time and it would have avoided probably at least 6 or 7 reformats/restores to Windows.  Ugh!  But I'm on dial up.  I'd just installed a new drive.  I didn't bother to do with installing sp2 before doing it because if it didn't work, it would be a pain in the rear end to have to do it again.  Ugh!  But I got it and it worked...and when the menu came up and I chose Windows, I sat there for God only knows how long with my eyes closed while it booted.  I was afraid to look. lol  If anyone else ever has this problem...MAKE SURE YOU HAVE SERVICE PACK 2!!!! lol

Thanks for all the help everyone and patience!!!

~*~ Ash ~*~

---

### Post by confused57 on 2006-07-29
Glad you got dual boot working...interesting about needing SP2...on to dialup.

---

