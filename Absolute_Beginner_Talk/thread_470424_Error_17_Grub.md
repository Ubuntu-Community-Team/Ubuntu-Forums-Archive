---
title: "Error 17 Grub"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by AuSpanky on 2007-06-11
I know that this sort of topic has been done to death, but ive pretty much read them all on this and other sites with no luck. I really dont want to be put off linux, but unfortunately if this install doesnt work i dont see myself trying it in the future. 

I started off with 3 sata hard drives. One with Windows XP and 2 NTFS drives. I cleaned one of them and installed ubuntu. But now i get the "error 17" error. I have looked and cant see what im doing wrong.

Ill start with the basic's. I have 3 sata hdd's:

sda: 200GB Windows
sdb: 500GB NTFS
sdc: 230GB (Linux)

My menu.lst:

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
# kopt=root=UUID=c2533156-cb06-404d-8955-6d14b0d25fc3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=c2533156-cb06-404d-8955-6d14b0d25fc3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=c2533156-cb06-404d-8955-6d14b0d25fc3 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

My device.map:

```

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

```

I thought it might have been something wrong with windows so i did something recommended in another thread with no luck -> [http://ubuntuforums.org/showpost.php?p=2811990&postcount=4](http://ubuntuforums.org/showpost.php?p=2811990&postcount=4)

If anyone can help or give some advice it would be much appeciated. At the very least i would like to get XP up and running. If you need more info just let me know.

---

### Post by HotShotDJ on 2007-06-11
Where is the rest of menu.lst??   There should be a bunch of stuff prior to the first line you posted.  If thats all you've got in the file, it is small wonder that it isn't working.

Here is my menu.lst to give you an idea of how it is supposed to look:
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
# kopt=root=UUID=d78e0bfc-f436-4b6f-b788-8b86a036a81e ro

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
# defoptions=quiet splash rootflags=data=writeback

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
# altoptions=(recovery mode) single rootflags=data=writeback

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
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d78e0bfc-f436-4b6f-b788-8b86a036a81e ro quiet splash rootflags=data=writeback
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d78e0bfc-f436-4b6f-b788-8b86a036a81e ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by AuSpanky on 2007-06-11
> **HotShotDJ said:**
> Where is the rest of menu.lst??   There should be a bunch of stuff prior to the first line you posted.  If thats all you've got in the file, it is small wonder that it isn't working.

Ive edited my first post to include the entire menu.lst.

---

### Post by confused57 on 2007-06-11
Open a terminal in the live cd & post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

You might want to try installing grub to your Ubuntu drive's mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
read the link, but it would something like this:
```
root (hd2,0)
setup (hd2)
```

then boot first to your Ubuntu drive, if you get a grub boot menu, highlight your Ubuntu entry, press "e", then change root from (hd2,0) to (hd0,0), then press "b" to boot...this is temporary, but you'll know if Ubuntu will boot with your system set up this way.

---

### Post by AuSpanky on 2007-06-11
Thanks onfused57, heres the output of fdisk -l. Ill try the temporary thing you suggested to see if it actually boots.

```

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24791   199133676    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      969018   488385040+   7  HPFS/NTFS

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30138   242083453+  83  Linux
/dev/sdc2           30139       30515     3028252+   5  Extended
/dev/sdc5           30139       30515     3028221   82  Linux swap / Solaris

```

EDIT: I did exactly what you said (changed it from (hd2,0) to (hd0,0)) and ive manged to boot into ubuntu. What does that mean?

---

### Post by confused57 on 2007-06-11
Even if the method(which is temporary) I mentioned works to boot first to your Ubuntu drive...you might want to read over this bios solution someone else found for grub error 17:
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)
you might want to set your boot order back the way you had it when you installed Ubuntu and try the bios suggestions in the link...if it doesn't work and booting first to your Ubuntu drive does, then you can set your system up to boot first to the Ubuntu drive and make permanent changes in your menu.lst.

Added:  Just saw your edit to your last reply...try the bios suggestion & post back if it doesn't work, unless you want to go ahead and set up your system to boot first to your Ubuntu drive.

---

### Post by AuSpanky on 2007-06-11
> **confused57 said:**
> Even if the method(which is temporary) I mentioned works to boot first to your Ubuntu drive...you might want to read over this bios solution someone else found for grub error 17:
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)
you might want to set your boot order back the way you had it when you installed Ubuntu and try the bios suggestions in the link...if it doesn't work and booting first to your Ubuntu drive does, then you can set your system up to boot first to the Ubuntu drive and make permanent changes in your menu.lst.

Added:  Just saw your edit to your last reply...try the bios suggestion & post back if it doesn't work, unless you want to go ahead and set up your system to boot first to your Ubuntu drive.

I was able to boot into ubuntu, however i had no luck booting into windows. If i setup my menu.lst would that also fix the windows issue?

---

### Post by confused57 on 2007-06-11
I probably won't be able to followup much longer tonight to help you, but I'll give you instructions to setting up your system, if you decide to boot first to your Ubuntu drive.

Boot into Ubuntu, edit your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
change the root entries from (hd2,0) to (hd0,0)

in the line beginning with #groot, change it to (hd0,0)

Then to boot your Window's, you'd need an entry similar to this:
```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

Your bios hard drive boot order would need to be sdc, sda, sdb.

You'll probably need to edit your device.map to reflect this change;
```
(hd0)  /dev/sdc
(hd1)  /dev/sda
(hd2)  /dev/sdb
```

These changes "should" boot your Windows on sda...what you might want to do is restore Window's IPL to your Window's mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
using one of the methods listed...then you would be able to boot your Window's drive independently of grub , by changing the boot order in bios

The Super Grub Disk is an excellent utility to boot Windows or Ubuntu and can restore Window's or Ubuntu's IPL to the mbr:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's a very small download(5-7 Mb), might take you all of 15 minutes to download & burn a copy to cd

---

### Post by AuSpanky on 2007-06-11
Thanks heaps for your help confused57. I'll have a look at your suggestions, but seeing as you probably wont be here long i thought i might ask one last question. Hypothetically lets say i just want to get rid of ubuntu for the time being. What would the best process be? Just run "fixmbr" ?

---

### Post by confused57 on 2007-06-11
> **AuSpanky said:**
> Thanks heaps for your help confused57. I'll have a look at your suggestions, but seeing as you probably wont be here long i thought i might ask one last question. Hypothetically lets say i just want to get rid of ubuntu for the time being. What would the best process be?
Use one of the methods in the link I gave you previously to restore your Window's IPL to your sda mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
then you can format or whatever you decide to do with your Ubuntu drive(sdc).

Here's how I have my system set up:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

which is basically how I was suggesting you might want to set your system up, but you'd be booting first to your Ubuntu drive on sdc and still be able to boot Windows independent of grub...good luck with it.

---

### Post by AuSpanky on 2007-06-11
lol ive manged to get booted back into windows and ive gotten rid of ubuntu. Thanks a million though confused57. Im sure not far down the track ill be giving it a go again.

---

