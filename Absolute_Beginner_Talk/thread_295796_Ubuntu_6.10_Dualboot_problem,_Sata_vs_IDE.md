---
title: "Ubuntu 6.10 Dualboot problem, Sata vs IDE"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by Dimitrion on 2006-11-08
Oke all you Ubuntu lovers, please help me out.

I'm totally new to linux, so my knowledge is nill.
Since my windows is illegal since i made some hardware changes, i'm looking in too working with Ubuntu.

My system contains one SATA harddisk and two IDE harddisks.
Windows XP pro is installed on the SATA.
The primary IDE is a data disk, wich contains my music, games and stuff like that.
The slave IDE is the one i installed Ubuntu on.
I installed Ubuntu 6.10 on an empty harddisk

I installed it standard using the live cd.

When i reboot grub gives me the following options:

Ubuntu
ubuntu (recovery)
ubuntu memorytest (or something like that)
Other Os
Win xp pro
Win XP pro

Only the last option works.
I cant startup ubuntu, when i try i get:

Error 17

:confused:

---

### Post by Dimitrion on 2006-11-08
i will post my fdisk -l
and my fstab
and my menu.lst

(yes, i did some reading :cool: )

Fdisk -l:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3648    29302528+   7  HPFS/NTFS
/dev/sda2            3649       38913   283266112+   f  W95 Ext'd (LBA)
/dev/sda5            3649       38913   283266081    7  HPFS/NTFS

Disk /dev/hda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       20023   160834716    7  HPFS/NTFS

Disk /dev/hdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        6997    56203371   83  Linux
/dev/hdb2            6998        7297     2409750    5  Extended
/dev/hdb5            6998        7297     2409718+  82  Linux swap / Solaris

---

### Post by Dimitrion on 2006-11-08
My menu.lst from hdb1

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
# kopt=root=UUID=c1268335-3fac-4319-b2fe-aafa11bbd7e6 ro
# kopt_2_6=root=/dev/hdb1 ro

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
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

---

### Post by Dimitrion on 2006-11-08
My fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=c1268335-3fac-4319-b2fe-aafa11bbd7e6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=98e3d097-0065-42a1-ab53-fec0ec8f0f86 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


Well, i did some nice cutting and pasting.
Really don't have a clue what it all means.
Any wise man who wishes to share its knowledge?
:D 
please

---

### Post by balaram on 2006-11-08
I'm not a moderator but I'm dual booted on several computers and have dealt with problems like these myself. The first thing I would do is the following. When Grub appears on your screen highlight the Ubuntu option and hit the letter e on your keyboard, that will bring up an edit screen, the top line should say something like 
root (hd1,0) in your situation that's what it should say based on the info you have on your post. if it doesn't appear and hopefully it won't then change it to read root (hd1,0) the instructions at the bottom of the Grub screen will explain how to edit the line in question. (hd1,0) is where the Linux OS is located.

---

### Post by gn2 on 2006-11-08
This thread may help: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

Where is Grub installed?

If it's on the Sata Windows drive, run fixmbr from recovery on Windows CD.

Then use Super Grub Disk to write Grub to the Ubuntu drive, with Windows drive disconnected.

Then put ubuntu drive first in the boot order, then either use F8 (or whatever key depending on BIOS) to boot Windows, or add Windows to the bottom of the Grub boot list.

More details in the thread.

---

### Post by Dimitrion on 2006-11-09
> **balaram said:**
> I'm not a moderator but I'm dual booted on several computers and have dealt with problems like these myself. The first thing I would do is the following. When Grub appears on your screen highlight the Ubuntu option and hit the letter e on your keyboard, that will bring up an edit screen, the top line should say something like 
root (hd1,0) in your situation that's what it should say based on the info you have on your post. if it doesn't appear and hopefully it won't then change it to read root (hd1,0) the instructions at the bottom of the Grub screen will explain how to edit the line in question. (hd1,0) is where the Linux OS is located.

Thanks for your reply.
Tried that what you suggested, unfortunately it already reads (hd1,0)

So that ain't it :-k

---

### Post by Dimitrion on 2006-11-09
> **gn2 said:**
> This thread may help: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

Where is Grub installed?

Dunno, how do i determine where grub is installed?
wait a sec; during install ubuntu tells me he installs it on hd0, helpfull?

---

### Post by Dimitrion on 2006-11-09
oi. can anyone tell me why menu.lst states i have two XP installations? because i don't.

(hd0); where grub was installed does not contain an OS. it's a data disk.
I guess grub should have installed it on (hd2,0), wich is my SATA disk with XP installed on it.
Can i change this (savely)?
Would it help?
:-k

---

### Post by gn2 on 2006-11-09
Hardware changes don't make your Windows illegal.

Just tell them your old hardware failed, and you had to fit some new parts.

Works for me, I'm on motherboard #3 with the same (legit) XP product key....

Super Grub Disk should help you fix Grub [http://adrian15.raulete.net/grub/tiki-pagehistory.php?page=En&diff2=3&diff_style=unidiff](http://adrian15.raulete.net/grub/tiki-pagehistory.php?page=En&diff2=3&diff_style=unidiff)

---

### Post by bulldog on 2006-11-09
For almost everything is a solution,but you make it hard on yourself.
Some basics,

When a computer has the possibillity of IDE **and** Sata you have to know your IDE disks come before your Sata disk.

So your IDE primary should be setup as a boot disk with an OS.
Your secondary IDE should be the data disk.
And your SATA can be set as first  boot device and have an OS but GRUB will see your primary IDE as the first boot disk anyway.

I would recommend to solve this issues first by switching your primary IDE with the secondary.

In that case you should have Ubuntu on the primary disk with GRUB on the secondary which is not going to work.
Now reinstall GRUB with the live cd.```
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
[code]sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
 ```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Grub will be installed to the mbr of the hdd which contains Ubuntu.
[/code]

Now you have to alter your fstab to set the changed hd's right,your partitions are not changed only hd0 becomes hd1 and vice versa.


Hope you can do something with this.

---

### Post by Dimitrion on 2006-11-09
> **gn2 said:**
> Hardware changes don't make your Windows illegal.

Just tell them your old hardware failed, and you had to fit some new parts.

Works for me, I'm on motherboard #3 with the same (legit) XP product key....

Super Grub Disk should help you fix Grub [http://adrian15.raulete.net/grub/tiki-pagehistory.php?page=En&diff2=3&diff_style=unidiff](http://adrian15.raulete.net/grub/tiki-pagehistory.php?page=En&diff2=3&diff_style=unidiff)

Well that didn't work for me. They told me that i was out of luck and that i had to purchase a new one.
They weren't even polite, even thinking about all the trouble i went through makes me spit with anger *vains start pulsing on the site of his head*
:evil:

---

### Post by Dimitrion on 2006-11-09
> **bulldog said:**
> For almost everything is a solution,but you make it hard on yourself.
Some basics,

When a computer has the possibillity of IDE **and** Sata you have to know your IDE disks come before your Sata disk.

So your IDE primary should be setup as a boot disk with an OS.
Your secondary IDE should be the data disk.
And your SATA can be set as first  boot device and have an OS but GRUB will see your primary IDE as the first boot disk anyway.

I would recommend to solve this issues first by switching your primary IDE with the secondary.

In that case you should have Ubuntu on the primary disk with GRUB on the secondary which is not going to work.
Now reinstall GRUB with the live cd.```
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
[code]sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
 ```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Grub will be installed to the mbr of the hdd which contains Ubuntu.
[/code]

Now you have to alter your fstab to set the changed hd's right,your partitions are not changed only hd0 becomes hd1 and vice versa.


Hope you can do something with this.

I'll give it a go
:D

---

### Post by Dimitrion on 2006-11-09
I changed my disks so ubuntu is primary
Reinstalled grub
But.....

For whatever reason i cant seem to get my fstab displayed.
I made a dir called ubunturescue
mkdir ubunturescue

i mount:
sudo mount -t ext3 /dev/hdb1 ubunturescue

i try to get fstab:
gedit /ubunturescue/etc/fstab

And i get a blanc screen
Please tell me i made a typo 
:-|

---

### Post by bulldog on 2006-11-09
Yep you did it wrong :D 

First find out the name of your existing Ubuntu install by```
sudo fdisk -l  (l as in like)
```


Boot the live cd and make a mount point```
sudo mkdir /mnt/rescue
```
Now mount your partition```
sudo mount dev/hd? /mnt/rescue
```

To get to your fstab```
gksudo gedit /mnt/rescue/boot/etc/fstab
```

Alter it and save the file.

---

### Post by anaconda on 2006-11-09
> **bulldog said:**
> When a computer has the possibillity of IDE **and** Sata you have to know your IDE disks come before your Sata disk.


Well actually this is not true with all computers (like mine for example) 

I had this exact same problem when I installed ubuntu the first time. ie. grub was installed correctly to the booting hd, but the hd0 hd1 and hd2 were a bit mixed up. eg. Grub tried to boot ubuntu from hd1, when it actually was in hd0. so ofcource the booting failed.

The solution was to manually edit the menu.lst -file so that the hd0, hd1 and hd2 were correct. 

so just change this:

title Ubuntu, kernel 2.6.17-10-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

to:
title Ubuntu, kernel 2.6.17-10-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

or this:
title Ubuntu, kernel 2.6.17-10-generic
root (hd2,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

in your menu.lst -file, or put all three to your menu.lst and try which of them works.

once you got that working then you want to change 
this line:
# groot=(hd1,0)
from your menu.lst -file accordingly, or you will have the same problem again when you install new kernel. (grub is reinstalled with each new kernel installation..)

---

### Post by pattymnaish on 2006-11-09
In the mkdir and mount commands, I think you need to replace "ubunturescue" with something like "/mnt/ubunturescure" or just "/ubunturescue". I hope that's clear...ish.

EDIT: Beat to it, as always.

---

### Post by Dimitrion on 2006-11-09
Seems the naming has changed while switching the disks.
Does this mean i have to change the fstab of (hda1)?
:-k 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3648    29302528+   7  HPFS/NTFS
/dev/sda2            3649       38913   283266112+   f  W95 Ext'd (LBA)
/dev/sda5            3649       38913   283266081    7  HPFS/NTFS

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6997    56203371   83  Linux
/dev/hda2            6998        7297     2409750    5  Extended
/dev/hda5            6998        7297     2409718+  82  Linux swap / Solaris

Disk /dev/hdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       20023   160834716    7  HPFS/NTFS

---

### Post by bulldog on 2006-11-09
> **anaconda said:**
> Well actually this is not true with all computers (like mine for example) 

I had this exact same problem when I installed ubuntu the first time. ie. grub was installed correctly to the booting hd, but the hd0 hd1 and hd2 were a bit mixed up. eg. Grub tried to boot ubuntu from hd1, when it actually was in hd0. so ofcource the booting failed.

Well I'm pretty sure it's the same on your computer :D 

The messing up appears when you set your Sata as first bootdevice.
Then the order of hd0 and so on get mixed up.

But if you install Ubuntu from the live cd I'm very sure it wil setup GRUB on your primary IDE disk.

---

### Post by Dimitrion on 2006-11-09
i mounted (hda1) 
here is the fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=c1268335-3fac-4319-b2fe-aafa11bbd7e6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=98e3d097-0065-42a1-ab53-fec0ec8f0f86 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


Is this still correct?
it reads:
# /dev/hdb1
shouldn't this be:
# /dev/hda1

and shouldn't:
# /dev/hdb5
be:
# /dev/hda5

:???:

---

### Post by bulldog on 2006-11-09
> **Dimitrion said:**
> Seems the naming has changed while switching the disks.
Does this mean i have to change the fstab of (hda1)?
:-k 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3648    29302528+   7  HPFS/NTFS
/dev/sda2            3649       38913   283266112+   f  W95 Ext'd (LBA)
/dev/sda5            3649       38913   283266081    7  HPFS/NTFS

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6997    56203371   83  Linux
/dev/hda2            6998        7297     2409750    5  Extended
/dev/hda5            6998        7297     2409718+  82  Linux swap / Solaris

Disk /dev/hdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       20023   160834716    7  HPFS/NTFS

Well it looks allright to me,just try to boot and see how it goes.

---

### Post by bulldog on 2006-11-09
> **Dimitrion said:**
> i mounted (hda1) 
here is the fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=c1268335-3fac-4319-b2fe-aafa11bbd7e6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=98e3d097-0065-42a1-ab53-fec0ec8f0f86 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


Is this still correct?
it reads:
# /dev/hdb1
shouldn't this be:
# /dev/hda1

and shouldn't:
# /dev/hdb5
be:
# /dev/hda5

:???:

Yes your hdb is switched to hda so you have to change it.

---

### Post by Dimitrion on 2006-11-09
anything else i have to change ?
or do i save and reboot?

---

### Post by bulldog on 2006-11-09
> **Dimitrion said:**
> anything else i have to change ?
or do i save and reboot?
 Im' not sure about the UUID thingy,youre running Edgy right?
It's possible it needs it to recognize the disk or something like that and maybe you have to switch the string too.

But as said,I,m not sure about it.

---

### Post by anaconda on 2006-11-09
if it didn't work check my advice again.

I might be wrong about the reason why the hd0 and hd1 were mixed, but mixed they were, and my solution fixed that problem.

Did you reinstall your grub after you made the modifications above.. you should..

---

### Post by cotcot on 2006-11-09
> **Dimitrion said:**
> I changed my disks so ubuntu is primary
Reinstalled grub
But.....

For whatever reason i cant seem to get my fstab displayed.
I made a dir called ubunturescue
mkdir ubunturescue

i mount:
sudo mount -t ext3 /dev/hdb1 ubunturescue

i try to get fstab:
gedit /ubunturescue/etc/fstab

And i get a blanc screen
Please tell me i made a typo 
:-|

Use gedit ```
ubunturescue/etc/fstab
```, not ```
gedit /ubunturescue/etc/fstab
```
Remark that the difference is only a "/". Without means that ubunturescue is in de home folder where you are when you boot the liveCD. With "/" means that it is a folder in the root. 
You can use /ubunturescue but than you have to create it using 
```
sudo mkdir /ubunturescue
```
Remark the sudo because you do not have the permission as normal user to create a new directory beyond the /home/user/

---

### Post by balaram on 2006-11-09
Well Dimitrion, what happened? Did you get it booted up?

---

### Post by Dimitrion on 2006-11-09
am at work at the moment, i left my pc running because i didn't had any more time.
Will see tomorrow and post my findings
:rolleyes:

---

### Post by Dimitrion on 2006-11-10
Oke, back home, time to test and restart the PC.

Grub menu appears: i choose to load Ubuntu.
Initially it starts to load!!
But...
then it reads:

Busybox v1.1.3 (Debian 1:1.1.3-2ubuntu3) build in shell (ash)
Enter 'help' for a list of build in commands

/bin/sh: can't acces tty; job control turned of
(initramfs)

:-k

---

### Post by Dimitrion on 2006-11-10
Anyone have a clue what i should do now?
:-?

---

### Post by bulldog on 2006-11-10
Boot the live cd and run ```
sudo update-grub
```

---

### Post by Dimitrion on 2006-11-10
And then restart?

---

### Post by Dimitrion on 2006-11-10
after starting up live cd
I open terminal and type:

sudo update-grub

Searching for GRUB installation directory ... 
No GRUB directory found.
 To create a template run 'mkdir /boot/grub' first.
 To install grub, install it manually or try the 'grub-install' command.
 ### Warning, grub-install is used to change your MBR. ###

(remember i'm new to this, please dont hate me for being a NooB)
;)

---

### Post by bulldog on 2006-11-10
Well being new is no excuse..........:D 

Okay I read it all over again.
We only switched 2 hard disk's which we should turn around in your fstab too.
We reinstalled GRUB to the first boot disk.
Now all should work!!

You don't have the Sata disk as a first bootdevice?

The order should be:first hd0 with GRUB and Ubuntu
                    second hd1 the data disk
                    thirth sda the windows disk

If you mess these around GRUB can't find what it's looking for.

---

### Post by Dimitrion on 2006-11-10
If memory serves me right, SATA is last in boot order
What harddisk should be first in booting order?
The one with ubuntu i guess?

---

### Post by bulldog on 2006-11-10
Well you should be sure :D 

The point is GRUB is counting your hd's and partitions.
When you change one hdd or add a partition GRUB can't do his job anymore.
So you have to be absolutely sure the boot order is right so GRUB can find it
files which are needed to boot.
For safety give us the output of```
sudo fdisk -l (l as in like)
```

Did you altered the UUID string in fstab?
Whasn't sure it should be needed but it could be.

---

### Post by Dimitrion on 2006-11-10
No i didn't alter the string (dont have a clue what it does)

here is my fdisk -l


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3648    29302528+   7  HPFS/NTFS
/dev/sda2            3649       38913   283266112+   f  W95 Ext'd (LBA)
/dev/sda5            3649       38913   283266081    7  HPFS/NTFS

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6997    56203371   83  Linux
/dev/hda2            6998        7297     2409750    5  Extended
/dev/hda5            6998        7297     2409718+  82  Linux swap / Solaris

Disk /dev/hdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       20023   160834716    7  HPFS/NTFS

---

### Post by bulldog on 2006-11-10
If I see this I have the idea your Sata is first boot disk it's at the top of the list.
Can you look in your BIOS and set the first IDE disk (hd0) as your first bootdevice to be sure.

If done look if GRUB appear on this disk,because if it's on an other disk all we are doing is guessing.

The string is an identifier I guess,but I'm not sure either.
But if you changed the hd0 and hd1 vice versa,you should change the string with it I guess.

---

### Post by Dimitrion on 2006-11-10
All I changed in fstab is hdb1 to hda1 and hdb5 to hda5.
i don't see any hd0 or hd1
I'm confused

---

### Post by bulldog on 2006-11-10
Your correct in fstab they called different as in menu.lst.

It's all rather simple you changed two drives from place,so you have to change it in fstab too.
We did only the UUID string not,so you can try that maybe it's some hd-id.

But I like to know if your Ubuntu hdd with GRUB is your **first**boot device,because if not,I'm guessing what to do.

---

### Post by Dimitrion on 2006-11-10
I rebooted and took a look
My (now)slave IDE was first boot
My (now) primary , with Ubuntu was second.
SATA last

I changed Ubuntu to boot first
I did get a grub menu, but when selecting to start ubuntu i get error 17 again.

Perhaps it's better to reinstall ubuntu on the new hardware setup instead of trying to change strings and stuff?

What do you think?

Oh and before i forget, to what location should i install grub when i get the option offered during install?
Simply (hd0) ?

---

### Post by balaram on 2006-11-10
I installed Edgy on a computer last night and its multi-booted; Windows and Dapper also. It has a SATA and two PATA drives in it just like yours. However I had to install all three OS on the SATA harddrive to get all three OS to boot.  In addition I must disconnect the two PATA drives when installing the OS or else Grub gets screwed up. After install i can re-connect the drives and everything works fine. I'm sure that guys who know what they're doing would never do it this way, but I'm not skilled at this stuff  I'm just happy to get things working.

---

### Post by bulldog on 2006-11-10
Well if you have the time to do it,it's fine by me.

I should install GRUB on the hdd where your Ubuntu is in your case hd0

It's really not that hard to do,but it's not that easy on a forum.
I'm sure if your computer was at my home I fixed it in half an hour.:D 

Your GRUB [menu.lst] and fstab should correspondent with your hdd configuration.
If you made a change to one of your hdd's you can easely change your fstab and/or menu.lst and everything should work like a charm.

But a reinstall should correct everything.

---

### Post by Dimitrion on 2006-11-10
Well it might not be as fun, but i hope to get things started.
Besides, fstab and menu.lst are the same as far as i can see.

I'm gonna try reinstall.

Will let you know what happens
:-D

---

### Post by Dimitrion on 2006-11-10
Oke, reinstalled.
No problems now.
Ubuntu starts up without any problems
Nice:cool: 

Seems the hardware change made all the difference.
So in the end±
install Ubuntu on your IDE primary drive.
Period

Glad i got it running
thanks all for all the advice
:D

---

### Post by Osamabingandhi on 2006-11-11
I seem to have the same problem as you grub returns error 17, i change mountpoint with e and hdd(0,1) and it starts up but get stuck for a few minutes and i get into busybox....I have only one sata and windows installed. I have tried xubuntu, kubuntu, and ubuntu in edgy and all get error 17.

About your windows problem, download a cracked copy. You have bought it and I for one think you have the right to use windows. Less money for microsoft...they have more than a couple of small countries and need no more. The restrictions they put on your product is not right.

---

### Post by bulldog on 2006-11-11
> **Osamabingandhi said:**
> I seem to have the same problem as you grub returns error 17, i change mountpoint with e and hdd(0,1) and it starts up but get stuck for a few minutes and i get into busybox....I have only one sata and windows installed. I have tried xubuntu, kubuntu, and ubuntu in edgy and all get error 17.

About your windows problem, download a cracked copy. You have bought it and I for one think you have the right to use windows. Less money for microsoft...they have more than a couple of small countries and need no more. The restrictions they put on your product is not right.

If you give the outcome of```
sudo fdisk -l  (l as in like
```
And your menu.lst```
cat /boot/grub/menu.lst
``` we can see if there's a fix for your problems.

---

### Post by drtvasudevan on 2006-11-12
from [http://www.gentoo.org/doc/en/grub-error-guide.xml](http://www.gentoo.org/doc/en/grub-error-guide.xml)

5. Grub Error 17

Situation

Code Listing 5.1: Grub Output

root (hd0,0)
filesystem type unknown partition type 0x7

Error 17 : Cannot mount selected partition

Solution

This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

Be sure to check your root(x,y) settings in your grub.conf.

Also, if you are trying to boot Windows, make sure that your grub.conf file has the root (hdX,Y) (or rootnoverify (hdX,Y)) and chainloader (hdX,Y)+1 in it.

---

### Post by cotcot on 2006-11-12
Dimitrion,

I fully agree with the approach of Bulldog.

Are you confortable with Bios and do you know how to enter your Bios and check (or change) the boot order so that the ubuntu disk becomes the first disk to boot ?
Can you give the boot order you have now ?

---

