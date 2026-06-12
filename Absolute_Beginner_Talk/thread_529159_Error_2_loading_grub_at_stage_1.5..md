---
title: "Error 2 loading grub at stage 1.5."
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by SnapyGapi on 2007-08-18
I have 250GB hard drive inside and 250GB external hard drive. I had windows vista installed on my computer, and then i decided, to install ubuntu too. I hardly installed it,( in partitioning, i used guided end selected my external drive). But now i cant boot windows or ubuntu. i can only use ubuntu live cd to get help from web.

When i turn my comp on it outputs this:

```
GRUB Loading stage1.5.

Grub loading, please wait...
Error 2
```

Heres my menu.lst file in /media/disk/boot/grub/ folder

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
# kopt=root=UUID=e941a4e5-043f-4937-b777-520317745f3e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e941a4e5-043f-4937-b777-520317745f3e ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e941a4e5-043f-4937-b777-520317745f3e ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

so please can anyone help?

---

### Post by src2206 on 2007-08-19
Hello

I am not a master of Ubuntu,  but I had once faced a similar GRUB loading error, and it was resolved by reinstalling Ubuntu grub.

SO I suggest that you try to reinstall GRUB and see whether your problem gets resolved.

---

### Post by crav on 2007-08-19
It's loading Windows off of Harddrive 0, partition 0 and Ubuntu off of Hardddrive 0, partition 1. You stated that the Ubuntu harddrive is in an external. If you have an internal drive, that's likely to be the one labled as your harddrive 0. You could either edit the menu.lst using the live cd, or you could reinstall grub.
Also, I'm not sure if Ubuntu will boot off an external drive. Even if it does, USB is *way* slower than IDE/SATA/WHATEVER

Hope all that helps. I fixed this error someone recently on my laptop while removing windows.

---

### Post by logos34 on 2007-08-19
Grub is on the internal as Crav said--the internal is 'hd0' (/dev/sda) and the external usb is 'hd1' (/dev/sdb).  Sata and usb use 'sd_'.  Grub will go to the internal drive by default despite the fact that you installed to the external.  Stage1.5 is on the root parition on the usb but for some reason grub can't pull it up, or something's all screwy with the MBR.  

Use SuperGrub CD to try to boot ubuntu and windows, and/or reinstall either bootloader:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

If your bios supports booting usb devices, you could put grub on the external drive and restore windows bootloader to the internal.

---

### Post by src2206 on 2007-08-19
> If your bios supports booting usb devices, you could put grub on the external drive and restore windows bootloader to the internal.

Does Fiesty support this option of installing GRUB in a USB pen drive? My motherboard supports booting from USB device, so if it does then I can use Ubuntu without the fear of messing windows installation.

Please tell me how this can be done.

---

### Post by logos34 on 2007-08-19
> **src2206 said:**
> Does Fiesty support this option of installing GRUB in a USB pen drive? My motherboard supports booting from USB device, so if it does then I can use Ubuntu without the fear of messing windows installation.

Please tell me how this can be done.

You could try these:

'Installing GRUB on a USB flash memory key'
[http://www.freesoftwaremagazine.com/articles/grub_intro/](http://www.freesoftwaremagazine.com/articles/grub_intro/)
(written for DSL but should be easy to adapt for Ubuntu)

OR

'How to make your Super Grub USB Disk In Ubuntu or other Linux'
1 - Installation of SGD in a USB device from a Linux with GRUB installed
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#bob](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#bob)

---

### Post by SnapyGapi on 2007-08-19
I did this:

```
sudo grub

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd1,0)

grub> root (hd1,0)

grub> setup (hd1,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd1,0) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

grub>  quit     
```


but its still the same...

root( <tab> returns:

```
grub> root (       #here i pressed <tab> key
 Possible disks are:  hd0 hd1

grub> root (hd
```

i wont on startup to be able to choose between windows and ubuntu (anyhow)

*the last option for me, would be to reinstall vista... but first i would like to try all options
*and i cant burn on cd or dvd, because the live cd is in.

---

### Post by confused57 on 2007-08-19
If you have a Vista install DVD(not a recovery disk), you could use the bootrec.exe utility to restore your internal hard drive's mbr:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by SnapyGapi on 2007-08-19
yes!!! it worked!!, but now it only loads vista, i dont have an option to choose between ubuntu and windows. should i use grub or windows boot loader and what is the difference?

and is this the problem for another thread?

---

### Post by confused57 on 2007-08-19
> **SnapyGapi said:**
> yes!!! it worked!!, but now it only loads vista, i dont have an option to choose between ubuntu and windows. should i use grub or windows boot loader and what is the difference?

and is this the problem for another thread?
Now that you're able to boot into Vista, I would recommend you burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's a very small download(5-7 Mb) and it "might" be able to boot Ubuntu on your external hard drive.

If SGD is unable to boot Ubuntu, you might want to read over this thread for installing to an external drive:
[http://ubuntuforums.org/showthread.php?t=226638&highlight=success+external](http://ubuntuforums.org/showthread.php?t=226638&highlight=success+external)
your bios would need to be capable of booting first to a USB device

EasyBCD is a utility for Vista that can boot Linux from Vista's bootloader:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

### Post by SnapyGapi on 2007-08-19
i burned SGD and boot from it, but i dont know how to use it...

i installed EasyBCD and under Add/remove entries added linux entry, and now i dont know which linux patition to use..

---

### Post by logos34 on 2007-08-19
> **SnapyGapi said:**
> i burned SGD and boot from it, but i dont know how to use it...

i installed EasyBCD and under Add/remove entries added linux entry, and now i dont know which linux patition to use..

SGD could stand some improvement to make it a little more user-friendly (IMO).

Isn't sdb1/(hd1,0) your linux root partition?

---

### Post by SnapyGapi on 2007-08-19
screenshot:
[[IMG]http://img388.imageshack.us/img388/2148/untitledla0.th.jpg[/IMG]](http://img388.imageshack.us/my.php?image=untitledla0.jpg)

---

### Post by logos34 on 2007-08-19
partition 0 (linux native) 230 GB

---

### Post by SnapyGapi on 2007-08-19
this was the first one to try, and on startup, it shows a menu, and if i choose linux, it doesnt load...

---

### Post by confused57 on 2007-08-19
> **SnapyGapi said:**
> this was the first one to try, and on startup, it shows a menu, and if i choose linux, it doesnt load...
For EasyBCD to boot linux, grub's IPL has to be installed to the root partition...you can do this with the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

"find /boot/grub/stage1" should return "root (hd1,0)", you would "setup (hd1,0)":
```
sudo grub
root (hd1,0)
setup (hd1,0)
quit
```

---

### Post by logos34 on 2007-08-19
> this was the first one to try, and on startup, it shows a menu, and if i choose linux, it doesnt load...

What if any error message/# pops up?

You've reinstalled Grub to the bootsector (not the MBR) of the linux root parition (hd1,0), as recommended, which is apparently the only way Vista bootloader will chainload Grub. 

Boot back into the ubuntu live cd and reinstall grub to the bootsector, but do 'setup' **twice** (see the neosmart page):
> 
[B]root (hd1,0)
setup (hd1,0)
setup (hd1,0)
quit[/B]

If that doesn't work, then go to plan B--boot directly from the USB drive.  But your Bios must support booting USB devices.  If yes then I'd reinstall grub to the MBR of the external drive and see it that gets you into ubuntu.  You can then edit menu.lst to try to boot Vista from grub.

---

### Post by logos34 on 2007-08-19
sorry confused57--once again I was typing away while you had already posted.

---

### Post by confused57 on 2007-08-19
> **logos34 said:**
> sorry confused57--once again I was typing away while you had already posted.
Hi logos34,  I typed my reply as fast as I could so I could get it posted before yours, just kidding...I like your idea of installing grub's IPL to the external hard drive's mbr & setting bios to boot the external drive before the internal drive.

---

### Post by logos34 on 2007-08-19
> **confused57 said:**
> Hi logos34,  I typed my reply as fast as I could so I could get it posted before yours....

I knew it!  (sneaky devil)

Seriously I gotta use the refresh button more often.

---

### Post by SnapyGapi on 2007-08-21
My bios:
1st FLOPPY DRIVE
HDD:PM-ST3250620AS
ATAPI CD-ROM
IDE:Optiarc DVD RW AD-7173A

(i have only one cd/dvd reader/writer)

find /boot/grub/stage1 returns hd(1,0)

so i did setup twice. And now it still loads vista on startup.

My menu.lst is located in external drive:
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
# kopt=root=UUID=e941a4e5-043f-4937-b777-520317745f3e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e941a4e5-043f-4937-b777-520317745f3e ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e941a4e5-043f-4937-b777-520317745f3e ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

What should i do next?

---

### Post by logos34 on 2007-08-21
> **SnapyGapi said:**
> My bios:
1st FLOPPY DRIVE
HDD:PM-ST3250620AS
ATAPI CD-ROM
IDE:Optiarc DVD RW AD-7173A

(i have only one cd/dvd reader/writer)

find /boot/grub/stage1 returns hd(1,0)

so i did setup twice. And now it still loads vista on startup.

My menu.lst is located in external drive:

...

**What should i do next**?

As I said in post #17:
> If that doesn't work, then go to plan B--boot directly from the USB drive.** But your Bios must support booting USB devices**. If yes then I'd reinstall grub to the MBR of the external drive and see it that gets you into ubuntu. You can then edit menu.lst to try to boot Vista from grub.

So if you can boot usb, go that route.  But remember: if you change the Bios **hard disk boot priority** (not to be confused with the device boot order which you listed above) so that your external USB drive is first, then it becomes '(hd0)', meaning you'll have to edit the 'groot' and 'root' lines in menu.lst, [add mapping to the windows vista entry]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk"), and finally swap drive designations in device.map to reflect the new bios order (mainly so that vista will boot). 

First, boot into the live cd again and change menu.lst:

Places>Home>double-click your linux root partition to mount (it will do so at '/media/disk').  

**sudo gedit /media/disk/boot/grub/menu.lst**

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=e941a4e5-043f-4937-b777-520317745f3e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd[COLOR="Red"]**0**[/COLOR],0)

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
root		(hd[COLOR="Red"]**0**[/COLOR],0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e941a4e5-043f-4937-b777-520317745f3e ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd[COLOR="Red"]**0**[/COLOR],0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e941a4e5-043f-4937-b777-520317745f3e ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd[COLOR="Red"]**0**[/COLOR],0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd[COLOR="Red"]**1**[/COLOR],0)
[COLOR="Red"][B]map            (hd0) (hd1)
map            (hd1) (hd0)[/B][/COLOR]
savedefault
makeactive
chainloader	+1


Then change **device.map**:

**sudo gedit /media/disk/boot/grub/device.map**

> (hd0) /dev/sdb
(hd1) /dev/sda

Finally, reinstall Grub to the USB drive MBR (I hope this doesn't conflict with the fact that it's already on the bootsector of the root partition, sdb1):

> sudo grub
root (hd1,0)
setup (hd1)       --->this puts it on the MBR, as opposed to what you did before, '(hd1,0)', which put it on the root partition
quit

(*N.B.: the usb drive is still at this point '(hd1)' until you change the order in the Bios)

Now reboot and enter the Bios.  **Change the USB drive to first in the hard disk boot priority**.  See if that gets you to the Grub menu on the external drive and from there into either OS.

Post back with the results and any questions.

---

### Post by src2206 on 2007-08-23
Thank you logos34 :)

As you said that it is possible to install Ubuntu GRUB in a CD, please post a link on the process.

---

### Post by logos34 on 2007-08-23
> **src2206 said:**
> Thank you logos34 :)

As you said that it is possible to install Ubuntu GRUB in a CD, please post a link on the process.

I sent you a PM.

But here's the link for anyone else that's interested:
[http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html](http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html)

---

### Post by CValentine on 2007-08-23
Or, if you don't care about installing Ubuntu again from scratch, follow my how-to here to get it right from the beginning...
[http://ubuntuforums.org/showthread.php?t=523861]("http://ubuntuforums.org/showthread.php?t=523861")

Regards,

CV

---

### Post by src2206 on 2007-08-23
Thank you logos34...thank you very much :) I sincerely appreciate your help. I shall surely give you the feedback.

Thank you CValentine, I shall surely check it out.

---

### Post by SnapyGapi on 2007-08-23
what here is usb?

1st FLOPPY DRIVE
HDD:PM-ST3250620AS
ATAPI CD-ROM
IDE:Optiarc DVD RW AD-7173A

---

### Post by logos34 on 2007-08-23
> **SnapyGapi said:**
> what here is usb?

1st FLOPPY DRIVE
HDD:PM-ST3250620AS
ATAPI CD-ROM
IDE:Optiarc DVD RW AD-7173A

There's a submenu for each class of storage device---like I said before go into the one for** hard drives** and change it.  Then the usb will show up in the device boot order in place of "PM-PM-ST3250620AS'

---

