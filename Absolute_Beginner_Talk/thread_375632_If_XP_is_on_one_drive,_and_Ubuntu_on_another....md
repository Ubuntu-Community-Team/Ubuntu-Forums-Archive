---
title: "If XP is on one drive, and Ubuntu on another..."
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by 94ranger on 2007-03-04
Guys,

I am wanting to install Ubuntu on a seperate drive from Windows. Windows is plugged into my first SATA plug. If Ubuntu is on the other hard drive, how will my system boot? Will it go straight into Windows every time, or will GRUB kick in and let me decide?

Thanks! I'm a n00b!

---

### Post by Patrick K on 2007-03-04
The second option you gave.

---

### Post by Kateikyoushi on 2007-03-04
Grub would kick in and you can decide, but if you do not like it can put grub on the second hdd and then you do not see it intul change to boot from second disk in BIOS, the live cd has limited control over the grub install.

May I ask is the other hdd a sata drive as well ?

---

### Post by 94ranger on 2007-03-04
Kateikyoushi,

Yes, both drive are SATA (they're both identical actually), and they are plug in the first and second SATA headers on the motheboard respectively.

I want to make sure I understand this before I potentially mess up my system: If XP is on SATA drive 1 and I install Ubuntu on SATA drive 2, my machine will load GRUB on bootup even though GRUB will be installed on drive 2 as well as the rest of Ubuntu. Correct? And GRUB will see WinXP on the first hard drive and give me the choice to boot from it, right?

Thanks guys! You all are quite helpful!

---

### Post by skyhopper88 on 2007-03-04
If you install grub to the second hd grub will only boot if you set the second hd to the boot first. Grub will then see Ubuntu and Windows on your other drive. If you install grub to the mbr of the first drive you must boot from your first HD. I recommend putting grub on the second hd and setting it to boot first in the bios so you don't mess with the mbr. It's what I do.

---

### Post by Kateikyoushi on 2007-03-04
I find booting from grub much more convy then changing the boot order especially if have to enter bios to change.
Grub will find your windows and automatically add it to the boot list. The live disc won't give you a choice where to install grub, but it isn't a big problem, even if you overwrite the XP mbr you can change it back in a few minutes if you have a windows cd.

---

### Post by punx45 on 2007-03-04
> **skyhopper88 said:**
> If you install grub to the second hd grub will only boot if you set the second hd to the boot first. Grub will then see Ubuntu and Windows on your other drive. If you install grub to the mbr of the first drive you must boot from your first HD. I recommend putting grub on the second hd and setting it to boot first in the bios so you don't mess with the mbr. It's what I do.

yes i agree with this option.   It is what I have set up as well.  (of course I haven't bothered to boot back into windows since i set it up :) )

---

### Post by 94ranger on 2007-03-05
Guys,

I appreciate the help so far. I think I've messed up somewhere. When it installed, it only allocated half of my HDD for the usable partition. I didn't know I could change this w/ the LiveCD, so I reinstalled it. Now, it cannot see the XP hard drive. I have moved the boot order but GRUB (1.5) still shows nothing.

I know my XP hard drive still has XP on it b/c the GNOME Partition Manager says that 40GB are still used, which is what I was using. Can anyone help this n00b out? Is there a way to reconfigure GRUB? GRUB was installed on hd0 (the Ubuntu hard drive). Do I need to reinstall (which I may do anyone b/c I accidently loaded the x86 install instead of downloading the 64 bit one)?

---

### Post by Kateikyoushi on 2007-03-05
I would stick with the x86 installer, less headaches.

could you post the output of this command ?

```
fidsk -l
```

---

### Post by confused57 on 2007-03-05
> **94ranger said:**
> Guys,

I appreciate the help so far. I think I've messed up somewhere. When it installed, it only allocated half of my HDD for the usable partition. I didn't know I could change this w/ the LiveCD, so I reinstalled it. Now, it cannot see the XP hard drive. I have moved the boot order but GRUB (1.5) still shows nothing.

I know my XP hard drive still has XP on it b/c the GNOME Partition Manager says that 40GB are still used, which is what I was using. Can anyone help this n00b out? Is there a way to reconfigure GRUB? GRUB was installed on hd0 (the Ubuntu hard drive). Do I need to reinstall (which I may do anyone b/c I accidently loaded the x86 install instead of downloading the 64 bit one)?
If I understand correctly, you're booting first to the Ubuntu drive and can boot Ubuntu, but there's no entry in your grub menu at bootup to boot Windows...if this is the case, you just need to add an entry to your /boot/grub/menu.lst:

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

Here's how to add an entry to your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

just add a Window's entry to the very end of the file...you might also want to read over this thread:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by 94ranger on 2007-03-05
Kateikyoushi,

When I ran fdisk -|, all I got was (and I know this isn't right):

james@james-ubuntu:~$ su fdisk -|
> 


confused57,
Thanks for the tip, but it didn't quite work! I read the post you linked to, and they said to put it above ###BEGIN AUTOMAGIC KERNEL LIST which is where I put it. Should I go there and at the end of the file? There is definatly a new entry called Windows XP, but when I select it, I get:

NTLDR is missing
Press Ctrl+Alt+Del to restart

What could I have done wrong to throw GRUB off? I coped your settings into the file. I've got a backup fortunatly.

Thank you all!

---

### Post by confused57 on 2007-03-05
> **94ranger said:**
> Kateikyoushi,

When I ran fdisk -|, all I got was (and I know this isn't right):

james@james-ubuntu:~$ su fdisk -|
> 


confused57,
Thanks for the tip, but it didn't quite work! I read the post you linked to, and they said to put it above ###BEGIN AUTOMAGIC KERNEL LIST which is where I put it. Should I go there and at the end of the file? There is definatly a new entry called Windows XP, but when I select it, I get:

NTLDR is missing
Press Ctrl+Alt+Del to restart

What could I have done wrong to throw GRUB off? I coped your settings into the file. I've got a backup fortunatly.

Thank you all!

The command "sudo fdisk -l"...the -l is a small "L", not a pipe(|).

You might want to post your menu.lst:
```
cat /boot/grub/menu.lst
```
it's possible your Windows root is pointing to the wrong partition.

If you want Windows to boot by default, place the entry above the ###BEGIN...., if it doesn't matter, then at the bottom of the file...you don't need both entries.

Does your Windows drive boot OK, if you select to boot to it first in bios?

---

### Post by 94ranger on 2007-03-05
Guys,
Here are my postings:

fdisk -l

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18700   150207718+  83  Linux
/dev/sda2           18701       19457     6080602+   5  Extended
/dev/sda5           18701       19457     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19456   156280288+   7  HPFS/NTFS
james@james-ubuntu:~$ 


When I set the Windows HDD to boot first, GRUB always takes over. I've even pulled the Ubuntu drive out, and the XP drive tells me to replace the boot disk. Before I reinstalled Ubuntu, this setup use to work just fine. I appreciate the help! Hopefully we can get this figured out!

menu.lst

james@james-ubuntu:/boot/grub$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=9960c103-a01b-489a-a56f-534a7720c1e1 ro
# kopt_2_6=root=/dev/sda1 ro

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

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

### END DEBIAN AUTOMAGIC KERNELS LIST
james@james-ubuntu:/boot/grub$

---

### Post by confused57 on 2007-03-05
It looks like grub installed to the Windows mbr somewhere along the way, this probably won't work, but you could try this entry:

title Windows XP test
rootnoverify (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

What you can do is just add this entry below your current Windows entry...it will show up in your grub menu at bootup as the 2nd Windows entry...if this doesn't boot Windows, you may have some extra work to get your Windows mbr restored.

If the 2nd entry doesn't work, you might want to disconnect your Ubuntu drive...may want to connect your Windows drive to sda & boot to it first in bios(connected as sdb may be fine, I don't know)...then repair the Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Hopefully, this is all you'll need to do to get your Windows drive to boot...if your NTLDR is indeed corrupted, you may need to also do FIXBOOT, as well as FIXMBR(which repairs mbr).

Added: You might also want to consider burning a copy of the Super Grub Disk(500 kb download):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it can restore Windows mbr & Linux grub and boot Windows or Linux

---

### Post by 94ranger on 2007-03-05
confused57,

I have tried adding those lines to the menu.lst and it did not work. I tried to use a Win98SE boot disk to run fidk /mbr, and I also tried my XP install disc and ran FIXBOOT and FIXMBR with no luck.

I am about to try GAG. Now, when I do this, should I leave both drives hooked up or just my confused XP drive?
Thanks for your help!

---

### Post by confused57 on 2007-03-06
> **94ranger said:**
> confused57,

I have tried adding those lines to the menu.lst and it did not work. I tried to use a Win98SE boot disk to run fidk /mbr, and I also tried my XP install disc and ran FIXBOOT and FIXMBR with no luck.

I am about to try GAG. Now, when I do this, should I leave both drives hooked up or just my confused XP drive?
Thanks for your help!
You should be able to leave both drives connected for GAG, I don't think GAG can boot your Linux drive unless grub is installed to the root partition.  Have you tried the Super Grub Disk?

---

### Post by 94ranger on 2007-03-06
No, I have not tried the Super Grub Disk. Actually I haven't tried either. Which do you think is easiest?
As far as GRUB goes, it's installed on the Linux hard drive as far as I know (Sorry for lack of knowledge!). I was hoping to leave the XP drive untouched when I did this. Next time I'll follow you're HowTo :)

---

### Post by confused57 on 2007-03-06
> **94ranger said:**
> No, I have not tried the Super Grub Disk. Actually I haven't tried either. Which do you think is easiest?
As far as GRUB goes, it's installed on the Linux hard drive as far as I know (Sorry for lack of knowledge!). I was hoping to leave the XP drive untouched when I did this. Next time I'll follow you're HowTo :)
If you've already downloaded & burned a copy of GAG, then you can try it...if you haven't downloaded either, then I'd suggest you try the Super Grub Disk first.  If SGD isn't able to boot your Windows, then try GAG...if neither one works, I'm not sure what you'd need to do other than reinstalling XP...you could try fixmbr & fixboot again with the Windows install cd.
I'm just not that experienced with recovering Windows...if I can find or think of anything else you can try, I'll post back.

I guess you could always connect your Windows drive to sda, set it in bios as the first hard drive in your boot sequence, then install Ubuntu to sdb & grub to sda...if I understand correctly this is how you initially set up your dual boot.  Probably won't work if your NTLDR is corrupted, but maybe worth trying...it's up to you.

I definitely prefer to have the hard drives be able to boot independently, by installing grub to the Ubuntu drive, booting first to the Ubuntu drive then booting Windows from grub.

Here's a good read about Windows bootloader & restoring:
[http://www.ubuntuforums.org/showpost.php?p=2250418&postcount=10](http://www.ubuntuforums.org/showpost.php?p=2250418&postcount=10)

---

