---
title: "Oops, dual booting vista/ubuntu mishap"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by pacguy on 2006-11-19
Hi all. Ubuntu newbie here with a bit of a messy problem. The other day I installed ubuntu and beryl, and boy was that fun. I partitioned my hd correctly and got ubuntu to work fine. The problem comes when I try to boot back into vista. A normal login gets to the screen with the loading bar and locks from there, while a safe mode start hangs at ccrdisk. I installed vista first and then partitioned my hd and installed ubuntu. My files that are left in the vista portion show up fine and I can access them with no problem. My guess is that the loader somehow got corrupted while installing ubuntu. I've looked through the forms but nothing seems to match this and being such a complete newb at this, it is difficult for me to understand what to do with out f****** up my computer more. Any help would be greatly appreciated.

---

### Post by ReaderRat on 2006-11-19
I am not familiar with Vista, but in any case, always back up everything important. About all I can do is give you some links:
GRUB - HowTo set/change the default OS in GRUB
          **[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)**
GRUB - How To Do Most Anything With GRUB
          **[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)**
GRUB - Restore GRUB after installing Win
          **[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)**
[[color=BLUE]**GRUB HowTo**[/color]](https://help.ubuntu.com/community/GrubHowto)

---

### Post by seshomaru samma on 2006-11-20
When the computer first boots do you have a Windows option in your Grub menu?

 please post your grub file here 
```
gedit /boot/grub/menu.lst
```

---

### Post by ReaderRat on 2006-11-20
You may have to "sudo" there
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by pacguy on 2006-11-20
When I start up the boot screen gives me  the options for ubuntu, ubuntu recovery, ubuntu memtest, other os, and vista/longhorn loader. Here is the grub file. Sorry for this, I don't know how to build in a text box. Also I tried to re-download vista rc1 and just install it to the windows partition but apparently the trail run for vista is over so I am fat outta luck. I'd like to avoid re-installing xp because if I did that I would have to re-install the second hd and lose all my data there. And that is just a tad to much trouble just to play oblivion.:rolleyes: 

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
# kopt=root=UUID=904dcd20-dc0d-455f-a1b0-9bfdf60ddd79 ro
# kopt_2_6=root=/dev/hdc2 ro

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdc2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdc2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by sailor2001 on 2006-11-20
in your 2nd para... you have no default # listed......default 0 would be linux, count down from there to windows system a put that # for your default.  I think that at the end of that paragraph you have to change the default # there also

---

### Post by sailor2001 on 2006-11-20
I should have been more precise (typing in the dark) go to terminal (applications/accessories/terminal) and copy/paste this sudo gedit /boot/grub/menu.lst  then change in 2nd paragraph the default number (this is the number for the system you want to boot up into, count down from 0 the sys you see as you startup) and then exit and it will ask you to save..most guys put the terminal in the toolbar so it's handy

---

### Post by pacguy on 2006-11-20
So in this paragraph
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

I just want to make sure I'm doing this right. Since windows is the fifth system on the start up screen I need to change the 0 to a 5. If I do that then will I still be able to restart and boot into ubuntu. Forgive me for being obtuse on this but I have no idea what I am supposed to do and I don't want to make things worse.

---

### Post by seshomaru samma on 2006-11-21
First make a back-up of your grub menu.lst
Then try this :
change this part 
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1
```
into
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title vista 
rootnoverify (hd0,2) 
chainloader +1
```
You might need to change the numbers in this line :
```
rootnoverify (hd0,2) 
```
according to how your partitions are set
i suspect it could be (hd0,0) depending if Vista is before Ubuntu on the hard disc or not

---

### Post by bodhi.zazen on 2006-11-21
If vista is on /dev/hdc1 you will need to use:

```
root (hd2,0)
```

(hdc1 = first partition on 3rd HD/device = (hd2,0) in grub speak)

---

### Post by ecmerkle on 2006-12-18
pacguy, did you ever solve this problem?  I am having a similar problem:

My entire hard disk was formatted ntfs with vista, so I defragmented the hard drive and then partitioned/installed ubuntu as a dual boot.  Ubuntu works great, and I can read the files on my vista partition.  When I try to boot into vista, though, the windows "file loading" bar pops up and just sits there forever.  I don't think this is a grub problem, because I can select vista from the menu and boot into it.  It just stalls once vista takes over.

i appreciate any tips/advice.

---

### Post by ecmerkle on 2006-12-18
I figured out my problem... the ubuntu respositories don't have the latest version of the ntfsprogs package, and only the latest version works with vista.  See:

[http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html)

So I first installed the latest version of ntfsprogs myself.  Then I ran ntfsfix on the vista partition, and it solved my problems.  I can boot into vista, and all is back to normal!

---

### Post by Saicho on 2007-03-28
I'm having the same problem.

When I tried the fix above,

```
sudo ntfsfix /dev/sda1
```

(/dev/sda1 is my Vista partition that is stalling on boot)

The partition was fixed, but when I try to boot back to Vista it still stalls on the green loading bar.

Any ideas?

---

### Post by Doug11 on 2007-03-28
> **pacguy said:**
> Hi all. Ubuntu newbie here with a bit of a messy problem. The other day I installed ubuntu and beryl, and boy was that fun. I partitioned my hd correctly and got ubuntu to work fine. The problem comes when I try to boot back into vista. A normal login gets to the screen with the loading bar and locks from there, while a safe mode start hangs at ccrdisk. I installed vista first and then partitioned my hd and installed ubuntu. My files that are left in the vista portion show up fine and I can access them with no problem. My guess is that the loader somehow got corrupted while installing ubuntu. I've looked through the forms but nothing seems to match this and being such a complete newb at this, it is difficult for me to understand what to do with out f****** up my computer more. Any help would be greatly appreciated.


My guess is that you resized your Vista partition with the partition editor on the ubuntu install cd. I did  this as well and had the exact same issure you are having. What worked for me is fairly simple, I booted into an old XP disc (not Vista-Vista didn't boot), I went about as I was going to do a fresh install, until I ogt to the point where it was going to reformat my drive. I then cancelled out of everything and booted back up and vista loaded with no problem. The only thing was my boot menu was gone and Vista was the only thing that would boot. No problem, all you have to do is a quick search on >restoring grub<there is a great how-to listed, only three or four simple commands in the terminal you will need to do when you load the Ubuntu Live CD and Voila, everything is back to normal. Well, at least it was for me. Hope it works if you haven't got it going already.

---

