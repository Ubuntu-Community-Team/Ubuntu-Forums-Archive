---
title: "[SOLVED] oh no! grub error :( :("
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by hait2 on 2007-11-21
i really really hope this can be fixed somehow
currently posting this from livecd of ubuntu..

so i was dual-booting xp/ubuntu, and i decided to run gparted (oh no). i noticed there were 2 partitions aside from xp,linux,linux swap, that were almost empty and a big chunk of unused space between them.

i copied the files from them to my linux partition (there was about 8mb or so), just to have a backup in case something happens (...) and deleted the partitions then i extended the linux partition to take up the unused space (about 22gb)

so.. i did *not* touch my xp partition at all, and only stretched my linux one.

anyway......
gparted crashed. that wasn't very nice
now i'm getting grub error 17 and am unable to boot neither xp nor ubuntu

i ran gparted from live to avoid mounting business.

i really really hope this can be fixed somehow >_<
ideas? please..

---

### Post by OffAxis on 2007-11-21
Straight off the grub website:
error 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

I'm guessing that when you stretched the linux partition and more importantly *eliminated* the partitions between the two that you changed the placement of the linux partition (so it's probably pointing at your swap space as the root).

So, boot to a live cd and backup your boot file

```
cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

then modify your menu.lst file to point to the appropriate partition(s).

```
nano /boot/grub/menu.lst
```

the default location for root is (hd0,0) where 
hd0 = hard drive #1
0 = the first partition 

Increment the partition # up until it gets to where it needs to be (probably (hd0,1) but it's dependent on how your partiitions are set up; ie. windows, linux, linux-swap.

---

### Post by hait2 on 2007-11-21
EDIT: sorry you posted while i was writing. ill try out your suggestion for now

here is some useful info i think
i don't know what to make of it

menu.lst file in ubuntu partition
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=5b767725-3241-4e04-a4bb-8ba3a1322fa9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5b767725-3241-4e04-a4bb-8ba3a1322fa9 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5b767725-3241-4e04-a4bb-8ba3a1322fa9 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1



output of fdisk -lu
> Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders, total 192426570 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       96389       48163+  de  Dell Utility
/dev/sda2   *       96390   114430994    57167302+   7  HPFS/NTFS
/dev/sda3       114430995   192426569    38997787+   f  W95 Ext'd (LBA)
/dev/sda5   *   114431121   143749619    14659249+  83  Linux
/dev/sda6       143749683   145131209      690763+  82  Linux swap / Solaris


---

### Post by OffAxis on 2007-11-21
ya, I slipped that in there about 30 seconds before you posted :D

---

### Post by hait2 on 2007-11-21
hmm this is strange

it doesn't find a menu.lst file yet i clearly see it if i file browse to it
i wonder where it's looking..

i think this is the problem
screenshot:
[http://img113.imageshack.us/img113/79/screenshotxf8.png](http://img113.imageshack.us/img113/79/screenshotxf8.png)

there is no grub folder in the left one??
disk is my windows, disk-1 is my ubuntu

disk-1 is in 
file system -> media->disk-1->boot
and has a grub folder with menu.lst

but the file system->boot
has no grub folder, and thus no menu.lst

i'm confused ;(

edit:
also, why the heck is everything in /media/ ? including disk?

oh man i think i royally messed something up :( :(

---

### Post by annda on 2007-11-21
> **hait2 said:**
> 
also, why the heck is everything in /media/ ?

you are writing this from a live cd, right? in that case everything will be mounted under /media.

try to boot from GRUB and edit the ubuntu line on the fly: select the ubuntu entry, hit 'e' and change root (hd0,5) to root (hd0,4) since now it's sda5 and the old system partition sda6 is swap. then hit 'b' to boot using the modified GRUB entry. if it works, change menu.lst to use root (hd0,4) instead of root (hd0,5).

if i understood your situation correctly, this should solve the problem.

---

### Post by hait2 on 2007-11-21
> **annda said:**
> you are writing this from a live cd, right? in that case everything will be mounted under /media.
ah ok thank you!

> **annda said:**
> 
try to boot from GRUB and edit the ubuntu line on the fly: select the ubuntu entry, hit 'e' and change root (hd0,5) to root (hd0,4) since now it's sda5 and the old system partition sda6 is swap. then hit 'b' to boot using the modified GRUB entry. if it works, change menu.lst to use root (hd0,4) instead of root (hd0,5).

sorry, what do you mean boot from grub? i don't have access to the grub menu as it spits out the grub error 17 when i boot. or do you mean something else?

man if i ever retrieve my OS's/data, the first thing i'm doing is buying an hdd to back up my files =/

---

### Post by annda on 2007-11-21
> **hait2 said:**
> 

sorry, what do you mean boot from grub? i don't have access to the grub menu as it spits out the grub error 17 when i boot. or do you mean something else?



i don't want to reboot now faking an error to verify this but i think you get error 17 after you actually select an entry and hit enter. i might be wrong, though. i haven't had it in a long time. you can modify the line by selecting it and hitting 'e' for 'edit' instead of enter.

if i am wrong, just go ahead and modify menu.lst on the hard drive using live cd. you are not going to lose any data by doing just that, in case you are worried.

---

### Post by hait2 on 2007-11-21
> **annda said:**
> i don't want to reboot now faking an error to verify this but i think you get error 17 after you actually select an entry and hit enter. i might be wrong, though. i haven't had it in a long time. you can modify the line by selecting it and hitting 'e' for 'edit' instead of enter.

if i am wrong, just go ahead and modify menu.lst on the hard drive using live cd. you are not going to lose any data by doing just that, in case you are worried.

no, i do not get access to the menu. it says something like 
loading grub 1.5
please wait

grub error 17

and that's it.

i'll try editing the menu.lst file to (hd0,4) as you suggested!

---

### Post by OffAxis on 2007-11-21
shouldn't it be (hd0,3)?

---

### Post by hait2 on 2007-11-21
> **OffAxis said:**
> shouldn't it be (hd0,3)?

well, i will try that then because (hd0,4) didn't work :(:(
thank you for your time and patience by the way guys, it's really very nice of you

rebooting again~

---

### Post by annda on 2007-11-21
> **OffAxis said:**
> shouldn't it be (hd0,3)?

i don't think so. his or her fdisk output says:

```
/dev/sda**5** * 114431121 143749619 14659249+ 83 Linux
```

---

### Post by hait2 on 2007-11-21
sorry i'm being an idiot i think

do i change this instance of (hd0,5)
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

b/c i was  changing the
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)

or both? or something else entirely

---

### Post by OffAxis on 2007-11-21
the # sign indicates a comment; anything after it is ignored.

So you were correct in changing it after the 
**title Ubuntu 7.10, kernel 2.6.22-14-generic**
line

---

### Post by hait2 on 2007-11-21
> **OffAxis said:**
> the # sign indicates a comment; anything after it is ignored.

So you were correct in changing it after the 
**title Ubuntu 7.10, kernel 2.6.22-14-generic**
line

so then what is the
[quote=menu.lst file]## DO NOT UNCOMMENT THEM, Just edit them to your needs[/quote]
mean? 

how would editing them help at all if you don't uncomment if they are ignored? or am i missing something here as well?

---

### Post by OffAxis on 2007-11-21
> i don't think so. his or her fdisk output says:

Code:

/dev/sda5 * 114431121 143749619 14659249+ 83 Linux



yes, but there's no sda4. Doesn't the grub partition count ignore the gap?
(bumping everything up 2 instead of 1?)

---

### Post by annda on 2007-11-21
it's just incorrect wording. i thing the author meant "don't uncomment the examples, edit REAL entries below"

by the way, change all instances of hd0,5 because they are all wrong. the other entries SEEM ok.

---

### Post by hait2 on 2007-11-21
well, i tried changing all the instance of (hd0,5) to 4 and 3 (even the commented groot one..)

but no luck, still same error

i'm not doing anything stupid like editing the wrong menu.lst file am i? 
at first my ubuntu and windows partitions aren't shown, so i have to go to explorer (where they show up as like 50GB Volume) and double click on it, at which point they're renamed to disk and disk-1.

it also depends on what order i click them so disk-1 could be my xp or my ubuntu..

anyway i go to media -> disk (or disk-1) -> boot ->grub -> sudo gedit menu.lst

and change that file
that's ok right?..
(there's some temp file menu.lst~, should i delete it?)

---

### Post by MegaJim on 2007-11-21
so you don't ever see the grub menu?

if that is the case, you need to reinstall grub from the terminal on your live cd:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by meierfra on 2007-11-21
In addition to changing all "root (hd0,5)" to "root (hd0,4)" you need to do two more things:

1)  Change "#groot (hd0,5)" to "#groot (hd0,4)"

Otherwise during the next kernel upgrade alll the "root (hd0,4)" will be changed back to "(hd0,5)".

2) Reinstall grub: In a terminal type:


```
sudo grub
```

This will give you a "grub>" prompt. Type

```
root (hd0,4)

setup (hd0)

quit

```

---

### Post by OffAxis on 2007-11-21
you just have 1 hard drive in the system, right?

---

### Post by hait2 on 2007-11-21
yes i just have the one hdd

---

### Post by OffAxis on 2007-11-21
is the boot flag still set?

you can fire up gparted and check (or enable it if necessary).

---

### Post by hait2 on 2007-11-21
> **meierfra said:**
> In addition to changing all "root (hd0,5)" to "root (hd0,4)" you need to do two more things:

1)  Change "#groot (hd0,5)" to "#groot (hd0,4)"

Otherwise during the next kernel upgrade alll the "root (hd0,4)" will be changed back to "(hd0,5)".

2) Reinstall grub: In a terminal type:


```
sudo grub
```

This will give you a "grub>" prompt. Type

```
root (hd0,4)

setup (hd0)

quit

```

THANK YOU VERY MUCH~!!!!!!!
the second step is what did it
so, curiosity speaks - what did the 2nd step do ? just reinstall grub/reset its settings? and/or what was my problem>_<

---

### Post by MegaJim on 2007-11-21
Grub resides on two places - the bootstrap code which is written into the MasterBootRecord, and the grub menu/loader code which sits on an ext2/3 partition on your disk.  Grub was looking for the second stage in the wrong location, and was therefore giving you error 17 as it couldn't find the menu and loader.

---

### Post by hait2 on 2007-11-21
> **MegaJim said:**
> Grub resides on two places - the bootstrap code which is written into the MasterBootRecord, and the grub menu/loader code which sits on an ext2/3 partition on your disk.  Grub was looking for the second stage in the wrong location, and was therefore giving you error 17 as it couldn't find the menu and loader.

aha, i see

ok thanks a lot everyone, i really appreciate it!

---

### Post by OffAxis on 2007-11-21
the 
```
root (hd0,4)
```
section sets the path

and
```
setup (hd0)
```
installs grub to the master boot record.

---

