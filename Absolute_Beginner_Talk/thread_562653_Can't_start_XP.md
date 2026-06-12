---
title: "Can't start XP"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by Howard Beale on 2007-09-29
Long story short: after installing Feisty Fawn I can't start up Windows XP. I suspect I messed up when I was creating a new partition. Any idea how I can fix this? Tweak the BIOS? Or is there something I can do in the Terminal?

BIG thanks in advance. And yes--so far I'm loving Ubuntu.

---

### Post by lisati on 2007-09-29
Do you remember what you told the install process when it asked how you wanted to organize the partitions?

---

### Post by Maestro23 on 2007-09-29
Post your menu.lst

> cat /boot/grub/menu.lst

and 

/etc/fstab

> cat /etc/fstab

---

### Post by bodhi.zazen on 2007-09-29
Ummm ... err ...

Can you give a better description of the problem or some additional information ?

When you boot you should see the grub, or boot menu with an option for windows ...

If so ... what happens when you select that option ? error message ?

If not ... can you post the output from this command in a terminal :
```
sudo fdisk -l
```

---

### Post by Howard Beale on 2007-09-29
Wow--some great replies. I don't have any boot menu that offers me a choice. I rushed through the installation and I'm paying for it now. 

This is what I got from Terminal:

brian@brian-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3647    29294496   83  Linux
/dev/hda2            3648        4243     4787370   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hdb2            1276        9728    67898722+   f  W95 Ext'd (LBA)
/dev/hdb5            1276        3825    20482843+   7  HPFS/NTFS
/dev/hdb6            3826        9728    47415816    7  HPFS/NTFS

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60800   488375968+   c  W95 FAT32 (LBA)
brian@brian-desktop:~$

---

### Post by bodhi.zazen on 2007-09-29
Any idea which of those partitions is your windows C:\

My guess would be /dev/hdb1

---

### Post by Howard Beale on 2007-09-29
> Any idea which of those partitions is your windows C:\

I'd guess the same:

/dev/hdb1 * 1 1275 10241406 7 HPFS/NTFS

---

### Post by bodhi.zazen on 2007-09-29
Well, assuming that is the case

Open a terminal and enter :

```
gksu gedit /boot/grub/menu.lst
```

Add a stanza for Windows & reboot. It there is already a menu for Windows, make sure the menu is not hidden on boot ...

> title Windows XP
root (hd1,0)
makeactive
chainloader +1

---

### Post by Howard Beale on 2007-09-29
> Open a terminal and enter :

Code:

gksu gedit /boot/grub/menu.lst



OK--done. I not have a window named "menu.Lst" and code I don't understand.

> Add a stanza for Windows & reboot. It there is already a menu for Windows, make sure the menu is not hidden on boot ...

Quote:
title Windows XP
root (hd1,0)
makeactive
chainloader +1


Painfully newbie here: I'm embarrassed to say I'm not sure how to do this second part. Where would I add the stanza--in the terminal window or the second window? And how would I add the stanza?

---

### Post by bodhi.zazen on 2007-09-29
LOL, I know the feeling.

The second window is gedit, an editor similar to notepad with a few enhancements.

The code you are looking at is geek for configuration of grub and takes a while to understand.

If you like you can look here : [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

====

OK, for the task at hand, scroll down, past all that code and geek speak ....

You will come to a few stanzas regarding Ubuntu

title Ubuntu
root (hdx,y)
kernel /boot blah blah blah
initrd /boot blah blah

Add the stanza for windows after the Ubuntu stanzas

Save, exit, reboot

---

### Post by lisati on 2007-09-29
> **bodhi.zazen said:**
> Any idea which of those partitions is your windows C:\

My guess would be /dev/hdb1

+1, because it's NTFS

---

### Post by Howard Beale on 2007-09-29
I tried the fix, but no go. 

I think there's a problem because of a previous fix I tried--copying text to gedit that was meant for a Windows Vista fix. Right now gedit gives me this:
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
# kopt=root=UUID=d38ddde9-1f90-4184-8174-2d7bb2e8a842 ro

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d38ddde9-1f90-4184-8174-2d7bb2e8a842 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d38ddde9-1f90-4184-8174-2d7bb2e8a842 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d38ddde9-1f90-4184-8174-2d7bb2e8a842 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d38ddde9-1f90-4184-8174-2d7bb2e8a842 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title Windows XP
root (hd1,0)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST# Windows Vista
title Microsoft Windows Vista
rootnoverify (hd0,0)
makeactive
chainloader +1

---

### Post by bodhi.zazen on 2007-09-29
No, I do not think so, although the vista stanza will not work ...

The "problem" is more likely a hidden menu

> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

When you boot you get no menu as it is hidden. To see a menu, press the <esc> key and select Windows XP.

If you want to see the menu without having to press <esc> change to :

> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

Note the # in front of hiddenmenu

If you get an error message when booting Windows, you may need to change to :

> title Windows XP
rootnoverify (hd1,0)
makeactive
chainloader +1

Post any error message ...

And, yes I would also comment out (add a # at the start of the line) the vista entry 

> # title Microsoft Windows Vista
# rootnoverify (hd0,0)
# makeactive
# chainloader +1

---

### Post by Howard Beale on 2007-09-29
Well, I'm getting closer, but it's still hanging up when I try to start Windows (the text "Starting Up . ." in the upper left corner of a black screen).

However, I've gotten rid of the Windows VIsta prompt on the OS selection menu. 

Again--I'm grateful for the help. If necessary, I can reinstall both OS's (I reinstalled Windows just last weekend).

---

### Post by bodhi.zazen on 2007-09-29
Try the rootnoverify option ...

> title Windows XP
rootnoverify (hd1,0)
makeactive
chainloader +1

If that fails we need to map your drives, like this :

> root (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

---

### Post by SpiritIsReality on 2007-09-29
howdy
bhodi.zazen ...thanks. please forgive me, but I can't help myself.  remote desktop assistance...? I'd like to see that! menu.lst timeout 7?
Howard Beale ...way to go pard. Hopin' YouAreInTheSaddle in no time.
all the best
trails

---

### Post by bodhi.zazen on 2007-09-29
> **fmat said:**
> howdy
bhodi.zazen ...thanks. please forgive me, but I can't help myself.  remote desktop assistance...? I'd like to see that!

:lolflag:

You know I can not resist answering that ... sorry Howard Beale for the diversion. If you want PM me and I will move these two posts out ...

Connecting Ubuntu -> Windows using remote Desktop (RDP) ?

Go to Applications -> Internet -> Terminal Server Client

[indent]In "computer" place your windows IP
In "Protocol" select "RDP" (This is the default)
Click "connect"
This will bring up a login box, enter windows user name and password -> viola[/indent]

You must configure Windows to accept a RDP session : 

[http://www.microsoft.com/windowsxp/using/mobility/getstarted/remoteintro.mspx](http://www.microsoft.com/windowsxp/using/mobility/getstarted/remoteintro.mspx)

If you have problems or this is not your question, please feel free to start a new thread as you are more likely to get help that way.

> menu.lst timeout 7?

This is how long, in seconds, grub wait for input before booting the default OS.

> Howard Beale ...way to go pard. Hopin' YouAreInTheSaddle in no time.
all the best
trails

---

