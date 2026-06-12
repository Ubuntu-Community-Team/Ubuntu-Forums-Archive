---
title: "GRUB doesn't list my windows partition!"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by alex-desktop79 on 2007-04-19
I just freshly installed Feisty Fawn. (It's amazing!)

For some reason GRUB only shows my Ubuntu partition, and I have to press ESC within 3 seconds to get to the menu. Any help?

---

### Post by askreet on 2007-04-19
Pressing ESC is normal configuration in Ubuntu.  You can modify that by running:

```

gksudo gedit /boot/grub/menu.lst

```

Find a line that says:
```

timeout  3

```

Change the timeout to something more appropriate, like 30.

If you don't want to have to press ESC, comment out this line:
```

hiddenmenu

```

If you want to add your windows partition, you'll have to find out what partition it's on.  To do that you can open up a terminal and type:
```

sudo fdisk -l

```

There should be a partition of type NTFS/HPFS.  That's your windows partition.  Getting the GRUB hard disk number for it can be tricky though.  Hopefully it's a single hard drive, then it's the same as your prior menu option.  Go back to your menu.lst file and find something like this:
```

title   Ubuntu kernel xxx
root   (hd0,0)
kernel    /blah/blah
etc..

```

If you copy this and paste it, you can create a new boot entry.  A windows boot entry looks like this:
```

title   Microsoft Windows XP Professional
rootnoverify  (hd0,0)
chainloader +1
boot

```

If your NTFS partition is /dev/sda3, then your root is (hd0,2).  If not, paste your fdisk -l output, along with your menu.lst here and I'll do what I can to help :)

Good luck!

---

### Post by alex-desktop79 on 2007-04-19
Just to be sure :)

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
# kopt=root=UUID=9d4323e7-51c3-4731-a593-09ff01a2c1f3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9d4323e7-51c3-4731-a593-09ff01a2c1f3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9d4323e7-51c3-4731-a593-09ff01a2c1f3 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```
and
```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20397   163838871    7  HPFS/NTFS
/dev/sda2           20398       24792    35302837+   f  W95 Ext'd (LBA)
/dev/sda5           20398       24721    34732467   83  Linux
/dev/sda6           24722       24792      570276   82  Linux swap / Solaris
```
It's all on one HDD :)

---

### Post by askreet on 2007-04-19
Right below this:
```

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9d4323e7-51c3-4731-a593-09ff01a2c1f3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

```

Add this:
```

title	Microsoft Windows XP
rootnoverify (hd0,0)
chainloader +1

```

If you want your last choice to be the new default choice you can add:
```

savedefault

```

Otherwise, Ubuntu will continue to be the default option.

Best of luck! :guitar:

---

### Post by alex-desktop79 on 2007-04-19
Thanks!

---

### Post by trubacca on 2008-02-12
> If your NTFS partition is /dev/sda3, then your root is (hd0,2).  If not, paste your fdisk -l output, along with your menu.lst here and I'll do what I can to help :)

Good luck!
Hi, I am still incredibly new at this "linux thing", I just got a new computer with a dual 64-bit AMD processor. For maximum compatibility with my other apps, I have to stick with 32-bit XP. However, I am quite interested in unlocking the potential of those 64-bit processors, so I installed the 64-bit flavour of Gutsy Gibbon. Quite nice! 
Problem is, I cannot get GRUB to find and load my Windows XP install anymore. My girlfriend is not too happy with me, so I need to fix this FAST. Let me give you the lowdown.
I have one 320gb hard drive. When it was still fresh, I partitioned it into 3 parts. 
C: WinXP 50GB
H: Vista 50GB
I: Storage 200GB

I decided to say goodbye to Vista and enter the fold of Ubuntu. I thought I did all the research, but the fact is I am not very experienced wit
h installing dual-boot systems.
here is the results of fdisk
> 
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3a583a58

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        6226    50002312+   f  W95 Ext'd (LBA)
/dev/sda2   *        6227       12249    48379747+  83  Linux
/dev/sda3           12634       38913   211094100    7  HPFS/NTFS
/dev/sda4           12250       12633     3084480   82  Linux swap / Solaris
/dev/sda5               2        6226    50002281    7  HPFS/NTFS

with /sda5 being my windows partition (C:)
I have no idea what sda1 is. honestly I don't.

I tried adding my installation in GRUB at (hd0,4) but when I tried booting, it just kind of... sat there. K, so I really am too much of a newb to want to screw around too extensively with the boot properties. 

Here is what my GRUB menu.lst file looks like,

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
# kopt=root=UUID=199c5bbd-7098-4e95-adaf-d8ce4cd3d156 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=199c5bbd-7098-4e95-adaf-d8ce4cd3d156 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=199c5bbd-7098-4e95-adaf-d8ce4cd3d156 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

title   	Microsoft Windows XP Professional
rootnoverify  	(hd0,4)
chainloader +1
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


Ya, anyway, I am sure that the problem is an easy fix. but I sure would love someone to give me a hand here. I am feeling kind of dumb. Like a stranger in a strange land. A vast alien landscape. I have been figuring out some commands in terminal. But honestly I have no clue what I am doing outside the GUI:confused:
Thanks in advance for your time!

______________________________________________________

---

### Post by skymera on 2008-02-12
i added this to get my windows working 
```
 
Winndoze XP Media Centre Edition
root            (hd1,0)
savedefault
makeactive
chainloader     +1
map (hd0) (hd1)
map (hd1) (hd0)

```

---

### Post by trubacca on 2008-02-12
No, I triedcopying that in and it didn't work. I tried fiddling around with the root settings (hd0,4),(hd0,0) and I tried taking out the map commands. I am afraid I am not very fluent with how linux organizes and labels hard drives and partitions. Thanks for your quick reply tho:confused:

---

### Post by ph1 on 2008-02-12
I'm not sure if this is important, but I always format it as (hd0,2), "0" referring to the number of your hard disk (I only have one, the "zeroeth" one) and "2" referring to the partition (Windows is on my second partition).  This is how I format mine whenever my grub gets replaced and I have to re-edit it:
 
title     Windows
root   (hd0,2)
savedefault
makeactive
chainloader +1

---

### Post by oedha on 2008-02-12
what if root (hd0,4)

---

### Post by ph1 on 2008-02-12
If Windows is on your 4th partition, then change it to (hd0,4).  Just put in whatever number Windows happens to be on.

---

### Post by trubacca on 2008-02-12
I appreciate your assistance. When I put in (hd0,4) grub says "Error 12: Invalid Device Requested"
I am pretty sure that is the proper hard drive. :confused:

---

### Post by oedha on 2008-02-12
mm.......have you try super grub disk ?

---

### Post by trubacca on 2008-02-12
I am trying to work with it right now, but no dice yet.

---

### Post by trubacca on 2008-02-12
Alright, after a good long while fidling with super grub, I have NOT succeeded. I Try to boot the windows partition and it says that it cant find the device.:confused::confused::confused: I know the partition is still alive and kicking because I can open the partition in ubuntu. I see no reason why this shouldn't be working, so I am as confused as ever. egads, my mind is burning out. I am going to continue screwing around with this here, so if I don't seem on-line, it is likely because I am busy rebooting. I will be sure to celebrate right here as soon as I succeed, so if it looks unresolved, that's because it is. But I REALLY REALLY appreciate everyone's help. Thanks!

---

### Post by trubacca on 2008-02-12
I think the solution to the problem lies in the fact that I get an "Error 12: Invalid Device Requested" every time I try to boot of of the windows partition (hd0,4).
I am trying to think of why Windows booted in the partition before Ubuntu, and now despite my best efforts cant boot it off of that partition anymore.:confused::confused::confused:

---

### Post by WildeBeest on 2008-02-13
I'm relatively a noob too, but have messed with the menu.lst file enough to be dangerous.

I believe your problem is the partition numbering. If windows is on your 4th partition, you would change it to (hd0,3). The partition entry is always zero based.

---

### Post by skymera on 2008-02-13
if your windows is 4th partition sure it would be (hd0,3) not (hd0,4)

---

### Post by trubacca on 2008-02-13
No guys, not quite. let me re-explain after a little bit more research. I have learned alot in the last 24 hours. Trial by fire, huh? Guess I am going to know more about linux than I had hoped!
Any, back to topic.
I don't know how, but windows is on a extended partition, the 5th partition according to fdisk, and is therefore (hd0,4). 
I am guessing that the Windows partition sda5 is a part of sda1, since the start and end blocks overlap.
I dunno if that helps solve the problem.
So... No matter what I do, I cannot (even by restoring the mbr with super grub or the windows recovery consol) get windows to boot. However, with the assistance of super grub, I can access the Ubuntu at any point. I am 90% certain that grub can do it, but that it is only a matter of configurations. I tried mapping hd0,4 to hd0,0 and vice versa, with rootnoverify hd0,0. It didn't work, but there might be some other configurations neccesary. I have been working with supergrub for hours (tried almost every option) but to no avail. I refuse to give up. But I need help. HELP ME NOT BE MURDERED BY MY GIRLFRIEND. perhaps more importantly, help me help my girlfriend appreciate linux! For fdisk -l readout check my first post.

---

### Post by ph1 on 2008-02-14
Trubacca, sorry to hear you've been through so much trouble.  Everything I could think to suggest you have already tried.  Is it possible that your copy of Windows has lost something important to its boot sequence?  (I don't know much about how Windows boots....)  Hopefully someone here who knows more than I can put in some better feedback.

---

### Post by trubacca on 2008-02-15
Hey ph1, Skymera, wildebeest, oedha, and others. Thanks! You provided much needed support and information in my attempts to solve my problem. Although the solution was much more involved than any single answer, I managed to put together a solution. Allow me to describe how I solved my problem, so that it may be preserved for future generations. 
NOTE: I am writing this the next day, so the steps may not be in a precise order. This is the general gist of what I did. I am also not entirely certain as to what is minimally necessary. I am still a little new at this.

The problem was that windows does not want to boot off of a logical partition.. unless it is the only operating system present. 
Step 1. What I had to do was create a primary partition formatted to NTFS, at least 4gb. MY hd had its max number of primary parts, but I did already have a primary NTFS partition- my 200gb storage partition.
Step 2. Use GParted to set the boot flag on the primary NTFS partition.
Step 3. Copy Windows directory from broken installation to the new NTFS partition. ( I don't know how necessary this is, but the other steps didn't work until I did this)
Step3.5. Copy ntldr and.. ntdetect.com(I think) to the root of your primary NTFS partition.
Step 4. Pop in the XP install cd and get into the recovery console
            type in FIXBOOT (not FIXMBR. FIXMBR will overwrite GRUB, and then you will need SuperGRUB to save you)
            FIXBOOT should write a new boot sector. I think it gives you a choice as to which drive you want to install it on. Make sure it gets put on the primary partition, if you can!
            If and when that works, go ahead and run BOOTCFG /REBUILD. In theory that should rebuild the boot.ini file.
           During this process it should find TWO (!) windoze installations (we fooled it!) and will ask you two questions.
          the first question asks what you want to designate the OS (for me the first OS was the new, fake installation. you can call it whatever you want. I chose NEO XP
          the second question is a little more complex. it asks you what options you want when the OS is loaded. I needed two switches. /FASTDETECT (Usually required) and /noexecute=optin (Used for buffer underrun protection for my processor Athlon 5200)

Step 5. IF this succesfuly completes, you are golden (almost).
             Go to your grub/menu.lst file and go to your windoze entry. Have the entry point at the primary windows partition.
Step 6. Reboot, use GRUB to choose windows, pray
If everything worked out properly, it should boot to windows. Mine did. 
I hope this helps anyone. I will elaborate on my process if anyone needs more information, or if I missed anything. I appreciate everyones help again. Thanks!          :)

---

