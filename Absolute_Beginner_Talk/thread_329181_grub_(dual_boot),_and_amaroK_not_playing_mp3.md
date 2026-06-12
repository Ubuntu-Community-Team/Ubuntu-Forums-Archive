---
title: "grub (dual boot), and amaroK not playing mp3"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by geo_bio on 2007-01-01
First, I am trying to use amaroK to play my mp3 files. However, it fails to play. I have installed the 5 gstreamer's (bad x2, ugly x2, ffmpeg), and I can get rhythmbox to play. It seems that amaroK uses something else (xine??) to play mp3, and I'm having a problem getting it to work.

Next, I just updated automatically (every few days, it asks me to update some files), and it asked me to restart. I restarted, and it showed up with grub. It seems that it crashed. It had one duplicate of the Ubuntu Kernel and and the recovery mode for the kernel. I tried to boot, and it had error 17 - where it cannot boot. Since this happened in the past (I was so annoyed that I updated and it all crashed), I know this time that all I had to do was to change boot option from (0,0) *which is my Windows partition* to (0,1). However, I'm not sure how often or why it would happen. It seems to happen (this is the second time) whenever I update. I **did** edit the grub menu.lst options myself. 

**This is my new menu.lst file that was edited after the error. Please tell me if I screwed up somewhere:**
```

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
default		4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=/dev/sda2 ro

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-27-386
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
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by Canis familiaris on 2007-01-01
amaroK requires some extra codecs to play MP3s.
Open terminal and input the following commands:
(Make sure your net connection is on)
> 
sudo apt-get install gstreamer0.10-plugins-ugly 
sudo apt-get install libxine-extracodecs

To get rid of all problems in codecs, Install automatix2 (read its license first).

**_[SIZE="4"] Installing Automatix2:[/SIZE]_**


> **_[SIZE="3"]Installing on (K,X)Ubuntu 6.06 i386,amd64 (Dapper)[/SIZE]_**

From terminal do the following (ONE LINE AT A TIME HITTING ENTER AFTER EACH STEP):

 echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main" | sudo tee -a /etc/apt/sources.list
 wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
 gpg --import key.gpg.asc
 gpg --export --armor 521A9C7C | sudo apt-key add -
[SIZE="2"]
To finish off:[/SIZE]

sudo apt-get update
sudo apt-get install automatix2


> [U]
**[SIZE="3"]Installing on (K,X)Ubuntu 6.10 i386,amd64 (Edgy)[/SIZE]**[/U]

From terminal do the following (ONE LINE AT A TIME HITTING ENTER AFTER EACH STEP):

 echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main" | sudo tee -a /etc/apt/sources.list
 wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
 gpg --import key.gpg.asc
 gpg --export --armor 521A9C7C | sudo apt-key add -

[SIZE="2"]To finish off:[/SIZE]

sudo apt-get update
sudo apt-get install automatix2



---

### Post by ajgreeny on 2007-01-01
Your grub error is because you have set the default to 4, which is the entry for other operating systems.  Change it to 5 and all should be OK again.  Seems silly I know, but the "Other operating systems" entry is counted even though it won't start any OS.

I'm assuming you can start windows if you select it in the grub menu, because I can't see any other obvious errors in the menu entries.

---

### Post by geo_bio on 2007-01-01
> **ajgreeny said:**
> Your grub error is because you have set the default to 4, which is the entry for other operating systems.  Change it to 5 and all should be OK again.  Seems silly I know, but the "Other operating systems" entry is counted even though it won't start any OS.

I'm assuming you can start windows if you select it in the grub menu, because I can't see any other obvious errors in the menu entries.

It was set to 5, but I later found out that numbering starts at zero (0). Therefore, the ubuntu kernels would be 0 and 1, the memtest is 2, the "other OS's" is 3, and windows is 4. 

**Correct me if I'm wrong and you're quite sure of it.**

---

### Post by ajgreeny on 2007-01-02
Whoops!  Sorry, you're right about that.  Not sure I can help further, sorry.

---

