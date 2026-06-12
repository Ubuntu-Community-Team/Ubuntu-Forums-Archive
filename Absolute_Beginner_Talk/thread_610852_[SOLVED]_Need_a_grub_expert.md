---
title: "[SOLVED] Need a grub expert"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by bumanie on 2007-11-12
This is a rehash of a post I made three days ago that has sat idle. Someone was going to send a possible fix, but have not posted again. So I thought I might try again. I am at work at present so can't post anything extra at present, but will show output for fdisk -l and grub menu.lst.
 
##fdisk -l output
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 11090 89080393+ 7 HPFS/NTFS
/dev/hda2 11091 11214 996030 82 Linux swap / Solaris
/dev/hda4 11215 15299 32812762+ 5 Extended
/dev/hda5 * 11215 15299 32812731 83 Linux

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
NB: dev/hda5 has been changed via cfdsik so it is no longer a boot

##grub menu.lst output

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d8ed1617-8917-471b-b114-f158568e08c3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title Ubuntu, kernel 2.6.20-16-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=d8ed1617-8917-471b-b114-f158568e08c3 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=d8ed1617-8917-471b-b114-f158568e08c3 ro single
initrd /boot/initrd.img-2.6.20-16-generic

title Ubuntu, kernel 2.6.20-15-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=d8ed1617-8917-471b-b114-f158568e08c3 ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=d8ed1617-8917-471b-b114-f158568e08c3 ro single
initrd /boot/initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

If anyone sees anything obvious re how to fix this, please post a reply and I will try it when I get home in a few hours.

---

### Post by LaRoza on 2007-11-12
Please post the problem too. I don't know what is wrong.

---

### Post by Duck2006 on 2007-11-12
That would help alot.

---

### Post by bumanie on 2007-11-12
Sorry, I hacked bits out of my original post and forgot to add the problem . Here it is:
Facts:
1) I have an amd 2600+ athlon, !gig ram, nvidia geforce 4 mx 4000 8x agp
2) I have a dual boot xp and feisty on master drive 
3) Everything was fine until I added a slave drive and attempted to install gutsy gibbon onto it
4) As soon as I installed gutsy, I immediately got grub error 17 which I fixed. I then tried loading gutsy again, thinking AI could fix grub again if things went wrong. I then got a grub error 22 at stage 1.5 of grub booting
5) I deleted the partitions on slave drive, thus removing gutsy
6) Grub is now mucked up. I continue to get grub error 22 at stage 1.5
7) Can only boot into an OS via super grub disk
 Super grub disk says it has been successful at restoring both xp and feisty, but grub error 22 continues, so I have to continue booting via super grub disk. Once booted both xp and feisty work perfectly. I am reasonably sure the problem is with the bootloader.

---

### Post by Duck2006 on 2007-11-12
Have you tryed # out the from this savedefault to this #savedefault
Does it only happen on linux or windows or both?

---

### Post by bumanie on 2007-11-12
Grub error 22 comes up immediately after the system check. I cannot get into either windoze or feisty without super grub disk. I haven't tried adding # to savedefault. Do you think it is that simple? I hope you are right. Would I have to do that on every savedefault listed?

---

### Post by maybeway36 on 2007-11-12
Can you reinstall GRUB to the hard drive (the one on your Feisty install)? I think GRUB is looking for Gutsy.

---

### Post by bumanie on 2007-11-12
> **maybeway36 said:**
> Can you reinstall GRUB to the hard drive (the one on your Feisty install)? I think GRUB is looking for Gutsy.
I have tried this via find /boot/grub/stage1 etc
output (hd0,4)
root (hd0,4)
setup (hd0)
quit
but this has made no difference.
PS: Grub error 22 occurred when gutsy was on slave drive, again I could get into it via sgd.

---

### Post by kellemes on 2007-11-12
Did you try the SuperGrubDisk-option of restoring Grub based on a present /boot/grub/menu.lst?
Assuming this menu.lst is correct this could work..

---

### Post by bumanie on 2007-11-12
> **kellemes said:**
> Did you try the SuperGrubDisk-option of restoring Grub based on a present /boot/grub/menu.lst?
Assuming this menu.lst is correct this could work..

As far as I can ascertain, I have tried all the GUI options on sgd. Ihaven't tried commands because I would not know what to enter.

---

### Post by jaybombalous on 2007-11-12
> **kellemes said:**
> Did you try the SuperGrubDisk-option of restoring Grub based on a present /boot/grub/menu.lst?
Assuming this menu.lst is correct this could work..


Ah, yes, that how one would re-generate a vmlinuz boot image??? Or whatever that file is called thats located in boot and is updated when u issue...   


```
sudo update-grub
```

---

### Post by bumanie on 2007-11-12
> **jaybombalous said:**
> Ah, yes, that how one would re-generate a vmlinuz boot image??? Or whatever that file is called thats located in boot and is updated when u issue...   


```
sudo update-grub
```

I have tried that too to no avail.

---

### Post by kellemes on 2007-11-12
I meant the restoration based on an existing menu.lst
I forgot the exact steps.. you don't need to enter commands at all.. just walk the menu.

The most informative page about this..
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Use_Super_Grub_Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Use_Super_Grub_Disk")

---

### Post by bumanie on 2007-11-12
> **kellemes said:**
> I meant the restoration based on an existing menu.lst
I forgot the exact steps.. you don't need to enter commands at all.. just walk the menu.

The most informative page about this..
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Use_Super_Grub_Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Use_Super_Grub_Disk")

I realised what you meant. As I said, I have tried all the options (at least I think I have) on sgd ie, those available on the gui. None have worked, although sgd thankfully boots the computer, it won't restore grub for some reason.

---

### Post by bumanie on 2007-11-12
This problem seems too hard to rectify. Maybe I will format and reload everything from scratch or keep using sgd until I get a new rig in the new year. However if nayone comes up with any more suggestions, I would be happy to try them.

---

### Post by philinux on 2007-11-12
you will get this error because you removed the partition I think

```
22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 
```

How to fix this in your case not sure.

[edit[ if I remember when I had this I had to disconnect the master thus making the slave master then installing linux on it.

---

### Post by philinux on 2007-11-12
I reckon after another think you need to boot the xp recover disk and do the fixmbr thing first.

---

### Post by jaybombalous on 2007-11-12
if u can get windows boot loader back on the MBR then u can always re-install grub while the slave is disconnected to make sure this doesn't happen again.

When I have two disk I write grub to both MBR and then use the bios on boot to select the disk I wanna boot from. On this bios its 'Esc' char.

---

### Post by bumanie on 2007-11-12
> **philinux said:**
> I reckon after another think you need to boot the xp recover disk and do the fixmbr thing first.

Thanks for the suggestion. I have tried that too!

---

### Post by bumanie on 2007-11-12
Have just got home from work. I have done another fdisk -lu, here it is
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   178160849    89080393+   7  HPFS/NTFS
/dev/hda2       178160850   180152909      996030   82  Linux swap / Solaris
/dev/hda4       180152910   245778434    32812762+   5  Extended
/dev/hda5   *   180152973   245778434    32812731   83  Linux

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System

Also did a update-grub as root, here is the output

 update-grub
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
cp: cannot remove `/boot/grub/menu.lst~': Permission denied
Does the last line give anyone any clues?

---

### Post by meierfra on 2007-11-12
In the bios: is your computer set to boot from the  the 160  GB  drive or from the 250 GB drive?

At boot-up:  Does the grub-menu appear? (Edit: I guess it  doesn't. See post #6))


> 
Also did a update-grub as root,
Did you do "sudo update-grub"  or did you activate the root account?

> 
cp: cannot remove `/boot/grub/menu.lst~': Permission denied

Post the output of 

```
ls -l /boot/grub
```

In your other thread you said that you tried booting with the slave drive unplugged, but that the boot-up was really slow. If you wait long enough, does the computer  eventually boot into ubuntu?

---

### Post by bumanie on 2007-11-13
Sorry not to answer earlier, but I work at night and had to sleep. To answer your question, the computer does eventually boot when the slave drive is unplugged.
Here is output of ls -l /boot/grub

total 224
lrwxrwxrwx 1 root root     31 2007-11-13 09:09 CRW_7206_14.xpm.gz -> splashimages/CRW_7206_14.xpm.gz
-rw-r--r-- 1 root root    197 2007-08-18 01:59 default
-rw-r--r-- 1 root root     15 2007-08-18 01:59 device.map
-rw-r--r-- 1 root root   8660 2007-08-18 01:59 e2fs_stage1_5
-rw-r--r-- 1 root root   8452 2007-08-18 01:59 fat_stage1_5
-rw-r--r-- 1 root root     15 2007-08-18 01:59 installed-version
-rw-r--r-- 1 root root   9152 2007-08-18 01:59 jfs_stage1_5
-rw-r--r-- 1 root root   4908 2007-11-13 09:10 menu.lst
-rw-r--r-- 1 root root   4908 2007-11-13 09:10 menu.lst~
-rw-r--r-- 1 root root   4908 2007-11-08 23:24 menu.lst-backup
-rw-r--r-- 1 root root   7860 2007-08-18 01:59 minix_stage1_5
-rw-r--r-- 1 root root  10132 2007-08-18 01:59 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2007-11-13 09:04 splashimages
-rw-r--r-- 1 root root    512 2007-08-18 01:59 stage1
-rw-r--r-- 1 root root 110132 2007-08-18 01:59 stage2
-rw-r--r-- 1 root root   9980 2007-08-18 01:59 xfs_stage1_5

---

### Post by meierfra on 2007-11-13
I have no idea what causes the "cannot remove `/boot/grub/menu.lst~': Permission denied "

But since your menu.lst looks fine, there really is no need to run "update-grub".

Currently I have two theories why you are not able get to the grub menu at boot-up

1) Your computer is trying to boot from the slave drive.

To fix this you would have to go into the bios and change the boot order.(Let me know if you need help with that)

2)  Your attempts to reinstall grub via " sudo grub, root (hd0,4) , setup (hd0) somehow failed.

Do this

sudo grub
root (hd0,4)
setup (hd0)
quit

but before "quit" copy the whole contents of the terminal and post it here. I want to see whether you are getting any error messages.

---

### Post by bumanie on 2007-11-13
I will look at bios again, but I believe it recognises both drives and is booting them in the correct order. In the meantime, here's the output of the code you suggested. 
   [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd0,4)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,4)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> root (hd0,4)

I will relook at bios now. Be back soon.

---

### Post by bumanie on 2007-11-13
O.K, I have checked bios. It recognises both drives. The boot order is 1st boot device cdrom; 2nd boot device is hdd-1; third boot device is hdd-2. I am still getting grub error 22. I am happy to try and unplug slave drive and try something with that out of the way if you wish.
PS: Is it possible that it is a kernel problem/conflict between fesity's kernel and gutsy's kernel. I have read a lot on the internet and although I have not found anything exactly the same as my problem kernel problems are often mentioned. Problem is I don't know where to start to edit things to fix this if it is in fact the problem.

---

### Post by meierfra on 2007-11-13
I don't have any good suggestion right now ( and I'm on my way  to bed).  Just to try something:  See what happens if  you change the boot order in the bios (hdd-2 before hdd-1)  I'll keep thinking about your case and let you know if I come up with something else to try.

---

### Post by bumanie on 2007-11-13
> **meierfra said:**
> I don't have any good suggestion right now ( and I'm on my way  to bed).  Just to try something:  See what happens if  you change the boot order in the bios (hdd-2 before hdd-1)  I'll keep thinking about your case and let you know if I come up with something else to try.

I will try that. I just found something on the internet I tried. Here is the output
$ uname -r
2.6.20-16-generic
ian@ian-:~$ cd /boot
ian@ian-:/boot$ ls vmlinuz
ls: vmlinuz: No such file or directory

Don't know if this helpful, but I think having no vmlinuz is most likely significant. I will search the internet further and see if I can track down anything about this. Of course if anyone reads this and has an idea of what I could try, please post instructions. I will be going back to work soon (10.5 hours + travel time). Won't be able to post any terminal outputs from work but can certainly answer any queries as to what I have tried and what I haven't. Thanking all who have tried to help.

---

### Post by bumanie on 2007-11-13
In addition to the above I have 'no command found' for /etc/fstab in terminal.
Here is the files contained within the boot folder in file system.
/boot/grub
/boot/abi-2.6.20-15-generic
/boot/abi-2.6.20-16-generic
/boot/config-2.6.20-15-generic
/boot/config-2.6.20-16-generic
/boot/initrd.img-2.6.20-15-generic
/boot/initrd.img-2.6.20-15-generic.bak
/boot/initrd.img-2.6.20-16-generic
/boot/initrd.img-2.6.20-16-generic.bak
/boot/memtest86+.bin
/boot/System.map-2.6.20-15-generic
/boot/System.map-2.6.20-16-generic
/boot/vmlinuz-2.6.20-15-generic
/boot/vmlinuz-2.6.20-16-generic

I cannot work out why I have  kernel 2.6.20-15-generic and 2.6.20-16-generic in the boot folder. Does this make sense to anyone? Is it normal or not?

---

### Post by bulldog on 2007-11-13
That is perfectly normal.
When you upgrade the kernel the old one isn't deleted automatically,if you want to delete it you have to do it yourself.

Can you describe your problem again?
As I understand you connected a second hdd,and now you're having problems to boot?
Is there anything more you've done besides connecting the hdd?

---

### Post by bumanie on 2007-11-13
The only thing I did initially was connect the slave drive and then install gutsy onto it. I believe it is hooked up correctly, as bios sees my original drive as master and the recently installed one as slave and identifies both by correct name and size etc. Following the install of gutsy, everything has been buggered up as far as grub goes.
To see the full history of the problem refer to the original post and read this one again, it will take too long to retype it all. Thanks. [http://ubuntuforums.org/showthread.php?t=605419](http://ubuntuforums.org/showthread.php?t=605419)

---

### Post by bulldog on 2007-11-13
Well you needed a GRUb expert,and actual I know my way around in dual or multiple booting.
If it's too much to ask what exactly the problem is,and if I have to read multiple pages to extract your problem and what you've done,I can't help you.

Basically,if you connect another hdd and install Gutsy on it,the question would be were was GRUB installed.
By default it will install on (hd0) and if the 'old' grub whas there,then you shouldn't have a problem.
You should be aware that by installing Gutsy,there was a new menu.lst created,which would list all the entry's in the 'old' menu.lst and add new lines for Gutsy.

If you just deleted gutsy,you can ```
sudo update-grub
``` to correct the menu.lst.


To reinstall grub you need the live cd.
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr[b] but be carefull here,if the find command returned (hd1,?)
the setup should be (hd1) not (hd0)!! [/b]
```
setup (hd0)
```
Exit the grub shell
```
quit
```

And I don't quite understanf this part.
```
Device Boot Start End Blocks Id System
NB: dev/hda5 has been changed via cfdsik so it is no longer a boot

```

---

### Post by bumanie on 2007-11-13
I have tried all those things already. 
Anything anyone has suggested to try, I still get the grub error 22.
Is it normal to have 'ls vmlinuz' to have no file or directory as an output.

---

### Post by bulldog on 2007-11-13
> **bumanie said:**
> I have tried all those things already. 
Anything anyone has suggested to try, I still get the grub error 22.
Is it normal to have 'ls vmlinuz' to have no file or directory as an output.
Yes because vmlinuz doesn't exist.
The command would be ls vmlinuz-2.6.20-16-generic

Edit:
22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 

I want you to select the boot option you want when you restart and see GRUB
Hit the  e  to edit this line
It should say (hd0,4) or something like that
Change the zero with a one so it would be (hd1,4)
Hit the b for boot and cross your fingers.

---

### Post by bumanie on 2007-11-13
As I mentioned one of my last posts, I am now at work and cannot generate anything from terminal for you to look at. However, from what I have already posted (from terminal), is there anything glaringly obvious as to why I keep getting grub error 22? Anyone who has tried to help, have all run out of ideas.

---

### Post by bulldog on 2007-11-13
> **bumanie said:**
> As I mentioned one of my last posts, I am now at work and cannot generate anything from terminal for you to look at. However, from what I have already posted (from terminal), is there anything glaringly obvious as to why I keep getting grub error 22? Anyone who has tried to help, have all run out of ideas.
 You can boot with ubuntu so it excist,only your menu.lst is wrong
I think your grub is on the other hdd and menu.lst should point at hd1,4 instead of hd0,4
Try it and see if it works.
If not,post back.

Edit again,lol
By installing gutsy,there whas a new grub installed as I explained.
This grub is most likely on the second hdd,but you deleted  gutsy with that menu.lst,but by deleting gutsy 
it won't delete grub.
So in other words,you have grub on both hdd's
If you dis connect the second hdd,you can boot,but by connecting the second hdd you can't [if I understand the problem,correct me if I'm wrong here]
This is because you boot from the second hdd and then is the menu.lst wrong as I stated.

---

### Post by ByteJuggler on 2007-11-13
Hey dude, I must apologise, I was away the weekend and subsequently kind of forgot about this thread (I keep a track on my subscribed threads by seeing which ones get new posts on them and the other one went quiet after I read your last post on it, and then I went and didn't respond as I normally do fairly shortly after.)  I'm at work at the moment, so can't give this attention right now, but I still have the VM I set up to troubleshoot this issue, so I'll try to get back to you tonight.   My apologies once again for being so tardy. :(

---

### Post by bumanie on 2007-11-13
> **bulldog said:**
> You can boot with ubuntu so it excist,only your menu.lst is wrong
I think your grub is on the other hdd and menu.lst should point at hd1,4 instead of hd0,4
Try it and see if it works.
If not,post back.

Edit again,lol
By installing gutsy,there whas a new grub installed as I explained.
This grub is most likely on the second hdd,but you deleted  gutsy with that menu.lst,but by deleting gutsy 
it won't delete grub.
So in other words,you have grub on both hdd's
If you dis connect the second hdd,you can boot,but by connecting the second hdd you can't [if I understand the problem,correct me if I'm wrong here]
This is because you boot from the second hdd and then is the menu.lst wrong as I stated.

It does not matter whether one or both the hard drives are connected, I still get the grub error 22. The only way I have been able to boot the computer for the past 2 weeks is via super grub disk. When gutsy was on the slave, grub was recorded as (hd1,2). Before I deleted gutsy, I tried to get grub to boot from there by coding root (hd1,2) setup (hd1) - I still got grub error 22. If I formatted the slave drive, this would get rid of gutsy's grub wouldn't it?

Do you think this would work, reinstall windows (I only keep it because the kids have M$ shoved down there throats from early primary school and they are resistant to using anything else), copy feisty to slave and then try to set up grub once feisty is on the slave. However, if I do that, maybe I should just reinstall both OS's from scratch. Windoze on master drive fesity on slave - I don't fell confident trying to install gutsy again, because until I tried installing it, everything was working perfectly. Don't know why I managed to configure a dual boot but can't get a  dual hard drive system working. Maybe gutsy is not the problem, but I have seen enough problems posted on this forum to indicate that there may well be some hardware conflict for some people, whilst others have upraded or done a fresh install without any problems. I also suspect my modem needs a firmware upgrade to be able to handle ipv6 - I think not having an ipv6 enabled modem ( although I did not know it was not enabled at the time of the install), did not help with the gutsy install as it stopped and hung at 82% when trying to connect ubuntu.com for updates. I just feel it is a shame to have to spend all that time reinstalling things that are otherwise working perfectly, however the amount of time I have spent trying to sort this out, probably equals the time to reinstall everything. I guess I have learnt some things about grub that I would not have known if this problem had not occurred, therefore I don't see this a waste of time. It is frustrating though!!!

---

### Post by bulldog on 2007-11-13
If you go for a complete reinstall,which should work,you have to keep some things in mind.
I see to many people who are getting frustrated,but it's there own mistake actual.

Some tips.
Dual boot windows and ubuntu and the best way of doing things.
Install windows first,than and this is important,make the windows hdd the slave device,or secondary master **but not the first hdd boot device in the BIOS**

Make the hdd which you'll install ubuntu ** the master boot hdd in yout BIOS**
Install ubuntu and let grub installon hd0 which is the ubuntu hdd.
GRUB will find your windows and add an entry for it in the menu.lst.

All should run from grub,and in case of a malfuntion of grub,you can boot windows by changing the master boot hdd in the BIOS.

Partitioning.
Most people let ubuntu do the partitioning,this will work,but it's not the best way to do it.
Because when you want to reinstall or what ever,you have to backup your /home first.
I would suggest to partition from the live cd or download the gparted live cd which you have to burn on a cd and boot from it.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Create two  10GB partitions
Create a partition for swap 1 a 2GB
Make the rest of the space one partition for /home
Install ubuntu by choosing manual when the partitioner asks.
Mount a 10GB partition as / for the file system,set bootflag enable and format ext3
Mount the swap as swap and format as swap
Mount your biggest [not the 10GB] partition as /home and format ext3
Proceed with the install

The biggest advantage is,your data is alway safe in your /home partition,except when the hdd is failing ofcourse.
You can try out a new distro,and not loose your existing one,by installing it on the spare 10GB partition,using the same swap and same /home.
Only thing to keep in mind,**never use the same login name as an existing install** so there will be a folder created within your /home for the new install,and not messing up your existing install.
You can copy,data between the two folders,like documents or what ever.

Okay that's about a new install.
But I'm not done with your problem yet.
You can boot using SGD,so there's nothing wrong with your ubuntu.
Only the boot part is messed up.

Try disconnecting the second hdd,then reinstall grub as I said and try to boot with just one hdd connected.
This has to work.
If so we'll take it from there to connect the second hdd.

---

### Post by bumanie on 2007-11-13
Okay that's about a new install.
But I'm not done with your problem yet.
You can boot using SGD,so there's nothing wrong with your ubuntu.
Only the boot part is messed up.

Try disconnecting the second hdd,then reinstall grub as I said and try to boot with just one hdd connected.
This has to work.
If so we'll take it from there to connect the second hdd.

I agree with you that it is only the boot part that is messed up. That's why I have perservered with trying to fix it. Windoze and feisty work fine once booted via sgd.

1) Thought it would not be so difficult.
2) Thought I would probably learn something (which I have), but unfortunately I haven't learnt how to fix the problem yet.

In response to your idea about disconnecting the second hdd and trying to reinstall grub, I have actually tried that both via live cd and from within feisty (once booted with sgd). It did not work. I did this 4 days ago as a result of a suggestion in the link I posted earlier. 
That's been the problem, everything everyone has suggested has failed. You do seem knowledgable about grub, did you check out the fdisk -l and the grub menu.lst at the start of this post?
 
The Device Boot Start End Blocks Id System
NB: dev/hda5 has been changed via cfdsik so it is no longer a boot is there again as a result of a suggestion from a forum member trying to help who suggeated I have only the windoze partition bootable. I can change this back to how it was if necessary.

---

### Post by bulldog on 2007-11-13
Change the bootflag back to the ubuntu partition please.

It is certainly not difficult!!
But you have to keep some things in mind.
When you installed Feisty you had one hdd.
Windows will recognize a new hdd,ubuntu will not,you can see the hdd,but it's not accesable by default.
Then you put in another hdd,no problem,but did you ever looked at how the jumpers on the back of the hdd are located?
If we're talkin about two IDE hdd's you can jumper them in different ways.
Both master...one as primary and one as secondary master
Master and slave one primary master other as primary slave
Master and secundary slave..one primary master and one secudary slave
There are a number of possibillitys how you can connect all this kind of devices,you can also have cable select,which requires a special cable and other jumper settings.
Not mentioning your cd-dvd-rom devices which has similar capabillitys.

How did you know the second hdd,if IDE,was the slave?
On which IDE chanel is this device connected?
Is there anything else on the same IDE chanel?

So you see questions enough.
The problem with a forum is to distract the right information.
When listening to multiple responders,and trying out there solutions,it's hard to find the right one.
Bottom line is,your ubuntu is boot able,the trouble started when you connected a new hdd,and installed gutsy.
Or better when you deleted gutsy.

From this part you'll have to go back to the basic.
One hdd which you didn't do anything to,no messing with cables or what ever.
If this is the case,you can make feisty boot again,because it did before.
It's all in the menu.lst.

---

### Post by bumanie on 2007-11-13
Bottom line is,your ubuntu is boot able,the trouble started when you connected a new hdd,and installed gutsy.
Or better when you deleted gutsy.
Get where you're coming from, but just let you know that I got the grub 22error as soon as gutsy rebooted from the live cd install - it did not start after gutsy was deleted, it was straight after the install.
Also just saw a post from byte juggler that's the dude who was attempting to set up a clone of my system via vmware. He went away for the weekend and forgot about it. But he has seen this thread and says he will try once he finishes work. I think either yourself or bytejuggler will sort this out. However, I will relook at how the slave drive is installed and look up the hdd manufacturers website to ensure things are right. Maybe I should put it on a seperate ide cable, as I have one use ide slot on the motherboard. What do you think?
Other thing, I am completely self taught, so I do at times make mistakes because I am often trying things that I work out on the fly. I will definitely check out the slave drive situation.

---

### Post by bulldog on 2007-11-13
Two hdd's should be set as primary master and secondary master,jumper settings both master.
Each with his own cable on a separate IDE port,do realize,one IDE is the master IDE and the other is the secondary IDE on the motherboard.
So connect them with care.

Cd and DVD device should be jumpert as slave in this setup,and in case you have more than one cd device,connect the fastest device on the master IDE hdd and the slowest on the secundary master.

In case of Sata devices you can forget all of this.
Sata devices are always masters and use a separate connection on the motherboard.
It's not really important on which connector,if you have a basic idea which hdd is which,although Sata ports are numbered too.
With this kind of devices you can simply setup in the BIOS which device you want to boot from,and in most cases you can set it once in the BIOS,and have the option to choose at boot time which device to boot by hitting some key,which will give you a list of all boot able devices.

So this was a free lesson,how do I setup my computer the right way :)

There is however the question of mixing Sata and IDE devices.
If you have two hdd's,one IDE and one Sata,trouble can be heading your way.
Because we have two primary masters here at stake.
Now you should know that in most cases,ubuntu will set the IDE hdd as the master and the Sata as slave.
This is not alway the truth,but you can fairly count on it.
So if you set the Sata as boot device and install ubuntu to the IDE hdd,you can think grub will be installed on the Sata hdd.
In most cases,you're wrong,grub will be installed on the IDE hdd.
So on reboot you're blowing right into windows and never see grub.
You have to set the IDE as master boot device to see grub,and edit the windows entry in menu.lst to boot windows again.

---

### Post by philinux on 2007-11-13
My dual boot system only has one cable connected to the two HD's.

---

### Post by bumanie on 2007-11-13
> **philinux said:**
> My dual boot system only has one cable connected to the two HD's.

That's how mine is at the moment. As iam not infront of my computer at the moment I am going on memory, but I think the slave is listed as a secondary slave during system startup. Would it be better to be a master slave or doesn't it make much difference?

---

### Post by bumanie on 2007-11-13
> **bulldog said:**
> Two hdd's should be set as primary master and secondary master,jumper settings both master.
Each with his own cable on a separate IDE port,do realize,one IDE is the master IDE and the other is the secondary IDE on the motherboard.
So connect them with care.

Cd and DVD device should be jumpert as slave in this setup,and in case you have more than one cd device,connect the fastest device on the master IDE hdd and the slowest on the secundary master.

In case of Sata devices you can forget all of this.
Sata devices are always masters and use a separate connection on the motherboard.
It's not really important on which connector,if you have a basic idea which hdd is which,although Sata ports are numbered too.
With this kind of devices you can simply setup in the BIOS which device you want to boot from,and in most cases you can set it once in the BIOS,and have the option to choose at boot time which device to boot by hitting some key,which will give you a list of all boot able devices.

So this was a free lesson,how do I setup my computer the right way :)

There is however the question of mixing Sata and IDE devices.
If you have two hdd's,one IDE and one Sata,trouble can be heading your way.
Because we have two primary masters here at stake.
Now you should know that in most cases,ubuntu will set the IDE hdd as the master and the Sata as slave.
This is not alway the truth,but you can fairly count on it.
So if you set the Sata as boot device and install ubuntu to the IDE hdd,you can think grub will be installed on the Sata hdd.
In most cases,you're wrong,grub will be installed on the IDE hdd.
So on reboot you're blowing right into windows and never see grub.
You have to set the IDE as master boot device to see grub,and edit the windows entry in menu.lst to boot windows again.

Thanks bulldog, that answers the question I just sent philinux (he's followed this saga for a while). Just for your information, I have 2 ide drives. Can you confirm you believe that they are best to be set up on seperate cables.

---

### Post by bulldog on 2007-11-13
> **philinux said:**
> My dual boot system only has one cable connected to the two HD's.

Never said this won't work,but it's not how it supposed to be.
For example,copying files from one disk to another has to go to the same cable and will slow things down.
If you use separate ports and cables,thing will be copied much faster.

Connect a cd-rom and a cd-burner to the same cable and IDE port.
Try to copy a cd on the fly,I'm pretty sure you can't do it.
It will copy it to your hdd first,and then burn it to the cd.

@TS 
Yes it's best to have separate cables and ports in use.
See my example above.

---

### Post by philinux on 2007-11-13
+1 bulldog, i was just commenting how mine was setup. A friend gave me the 120gig drive and also gave me a cable with it. He told me it was a low loss ide cable or something. 

Just checked my bios 

Primary IDE Master - linux drive
Primary IDE Slave   - Windoze

I cant for the life of remember how I set the jumpers though.

Since August have not used the windoze drive.

---

### Post by bumanie on 2007-11-13
Connect a cd-rom and a cd-burner to the same cable and IDE port.
Try to copy a cd on the fly,I'm pretty sure you can't do it.
It will copy it to your hdd first,and then burn it to the cd.
I must disagree with this. I have a dvd burner and cd burner on the same cable have copied on the fly in windoze using cd clone (I think that's the program). It worked fine for what I did, which was backing my son's text book cd-roms for school. Carrying such things around often wrecks them.

Any way, I'll take your advice and get a new ide cable tomorrow and set the slave as a master slave (if I can manage to!)

---

### Post by bulldog on 2007-11-13
> **philinux said:**
> +1 bulldog, i was just commenting how mine was setup. A friend gave me the 120gig drive and also gave me a cable with it. He told me it was a low loss ide cable or something. 

Just checked my bios 

Primary IDE Master - linux drive
Primary IDE Slave   - Windoze

I cant for the life of remember how I set the jumpers though.

Since August have not used the windoze drive.

This is 'wrong' it should be:
primary IDE master -linux  --> this is good
secundary IDE master -windows --> this one is wrong

And your cd-rom would be primary IDE slave

---

### Post by bulldog on 2007-11-13
> **bumanie said:**
> Connect a cd-rom and a cd-burner to the same cable and IDE port.
Try to copy a cd on the fly,I'm pretty sure you can't do it.
It will copy it to your hdd first,and then burn it to the cd.
I must disagree with this. I have a dvd burner and cd burner on the same cable have copied on the fly in windoze using cd clone (I think that's the program). It worked fine for what I did, which was backing my son's text book cd-roms for school. Carrying such things around often wrecks them.

Any way, I'll take your advice and get a new ide cable tomorrow and set the slave as a master slave (if I can manage to!)

Well maybe it changed over time,but when I did the lasttime [6 years ago I guess] this couldn't be done,I'm  talkin about copying a fair amount of data 600MB 
What I know is,it will copy the data to the hdd and from there to the burner.
If you do it again,have a close look in what's going on.:)
Maybe we mis understood each other.
On the fly means straight from one cd to another,without the use of any hdd.
Ofcourse you can copy cd's with them both on one cable,only it takes more time.

---

### Post by philinux on 2007-11-13
Just checked my bios again.

Primary IDE Master - linux drive
Primary IDE Slave - Windoze

Secondary IDE Master is my DVD player
Secondary IDE Slave is my CD- RW drive.

Dont know if its wrong but everything works as it should :confused:

---

### Post by bumanie on 2007-11-13
> **bulldog said:**
> This is 'wrong' it should be:
primary IDE master -linux  --> this is good
secundary IDE master -windows --> this one is wrong

And your cd-rom would be primary IDE slave

Sorry. That is not how mine is setup. Mine has windoze on first partition of master drive, swap and feisty on hd0,2; hd0,4 repectively. Gutsy was going to be on 250 gig slave by itself. My drives are on the same cable though, but I will change that later today.

---

### Post by bulldog on 2007-11-13
> **philinux said:**
> Just checked my bios again.

Primary IDE Master - linux drive
Primary IDE Slave - Windoze

Secondary IDE Master is my DVD player
Secondary IDE Slave is my CD- RW drive.

Dont know if its wrong but everything works as it should :confused:

This is not wrong in the sence 'it won't work'
Yes this will work,only it can be done quicker if you setup things 'right'
In your case I would,but I like building computers,change things,but if it works alright for you,just let it be.

---

### Post by philinux on 2007-11-13
```
Sorry. That is not how mine is setup. Mine has windoze on first partition of master drive, swap and feisty on hd0,2; hd0,4 repectively. Gutsy was going to be on 250 gig slave by itself. My drives are on the same cable though, but I will change that later today.
```

If I remember a poster on here he said its better to just have windows on its own drive. Obvious installed first. Then for the other drive he had an extended partition with lots of small logical partitions which he had about 6 distros on.

---

### Post by bulldog on 2007-11-13
> **bumanie said:**
> Sorry. That is not how mine is setup. Mine has windoze on first partition of master drive, swap and feisty on hd0,2; hd0,4 repectively. Gutsy was going to be on 250 gig slave by itself. My drives are on the same cable though, but I will change that later today.

The partitions are not important it this story,we are discussing how a computer should be build.

Will give another last example.
What should travel faster,500 cars on one small street or 500 cars on two small streets.
Because the hdd's are the most used from the four devices,you have to give them the opportunity to work the best.
This is done by making them both master on different IDE ports.
Your cd devices are much less used,so they can do with the slave function.
But don't change your working computer because I say so,I only tell how you get the best out of it,because I'm interested in performance.

---

### Post by bulldog on 2007-11-13
> **philinux said:**
> ```
Sorry. That is not how mine is setup. Mine has windoze on first partition of master drive, swap and feisty on hd0,2; hd0,4 repectively. Gutsy was going to be on 250 gig slave by itself. My drives are on the same cable though, but I will change that later today.
```

If I remember a poster on here he said its better to just have windows on its own drive. Obvious installed first. Then for the other drive he had an extended partition with lots of small logical partitions which he had about 6 distros on.

That could have been me :)
I run five different OS's on my computer at the moment,and one in Virtual Box

---

### Post by philinux on 2007-11-13
LOL bulldog, I think that way grub wont get messed up ?

---

### Post by bulldog on 2007-11-13
> **philinux said:**
> LOL bulldog, I think that way grub wont get messed up ?

Not a chance :)
I had trouble with grub once,and was sick of it.
Did my reading and testing,and it's not so hard to understand.
Grub reads only a list,menu.lst,to know were your boot partitions are located,and boot the one you want.
You only have to make sure the parameters are correct.

On the forums I ran into other users with a different setup,and I learned a lot.
Take a look at Herman's grub page,you will be amaze what you can do.
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by bumanie on 2007-11-13
> **philinux said:**
> LOL bulldog, I think that way grub wont get messed up ?

Running so many OS's on one box, maybe that is why bulldog knows the 'correct' way to set up hdd's and knows how to get grub working.

---

### Post by bulldog on 2007-11-13
> **bumanie said:**
> Running so many OS's on one box, maybe that is why bulldog knows the 'correct' way to set up hdd's and knows how to get grub working.

The OS's are not the problem,keeping the hard drives not mixed up when I have to replace something.
That is messing things up,especially if you have two or more identical hdd's in the computer.
But because I know what I did wrong,I won't panic and am able to correct things.
I have three hdd's all seagate two identical 320GB and one 500GB.
Wanted always test a RAID setup,but haven't found the time.

---

### Post by bumanie on 2007-11-13
I have left the hard drives as primary master (xp;feisty) secondary slave

sudo fdisk -lu
Password:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63   178160849    89080393+   7  HPFS/NTFS
/dev/hda2       178160850   180152909      996030   82  Linux swap / Solaris
/dev/hda4       180152910   245778434    32812762+   5  Extended
/dev/hda5   *   180152973   245778434    32812731   83  Linux

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

---

### Post by bulldog on 2007-11-13
Can you disconnect the second hdd?

Nice,now boot and select the feisty option in your grub and try to boot.
Look for any error.

---

### Post by bumanie on 2007-11-13
Booted as per normal that time bulldog, that is with the 2nd hdd unplugged. Don't why it wouldn't do that last time I tried that anyway it did it this time.

---

### Post by ByteJuggler on 2007-11-13
OK so, this is being posted from a VM that has the same disk layout as yours, I've not yet tried to install Gutsy to see if I can replicate the problems, but since this machine still boots etc, I'll first post the files etc from this one so you can try fixing using this information.  Firstly, here's output from "fdisk -lu" so you can see exactly which partitions I've got marked as active and so on:

```
walterp@VM1:~$ sudo fdisk -lu

Disk /dev/hda: 12.8 GB, 12884901888 bytes
255 heads, 63 sectors/track, 1566 cylinders, total 25165824 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    12675284     6337611    7  HPFS/NTFS
/dev/hda2        12675285    13671314      498015   82  Linux swap / Solaris
/dev/hda3        13671315    25157789     5743237+   5  Extended
/dev/hda5        13671378    25157789     5743206   83  Linux

Disk /dev/hdb: 6442 MB, 6442450944 bytes
16 heads, 63 sectors/track, 12483 cylinders, total 12582912 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
walterp@VM1:~$ 
```

If you want to match this setup exactly you'll need to set the bootable flag on the Windows partition as above.  Then, here's my /boot/grub/menu.lst:

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
# kopt=root=UUID=0c4491c7-3629-4a25-8f15-d35e5953fe49 ro

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
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0c4491c7-3629-4a25-8f15-d35e5953fe49 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0c4491c7-3629-4a25-8f15-d35e5953fe49 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

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

```

My device.map file:

```
(hd0)	/dev/hda
```

Contents of the /boot and /boot/grub folders:

```
walterp@VM1:~$ cd /boot
walterp@VM1:/boot$ ls
abi-2.6.20-15-generic         initrd.img-2.6.20-15-generic.bak
config-2.6.20-15-generic      memtest86+.bin
grub                          System.map-2.6.20-15-generic
initrd.img-2.6.20-15-generic  vmlinuz-2.6.20-15-generic
walterp@VM1:/boot$ ls grub
default        installed-version  minix_stage1_5     xfs_stage1_5
device.map     jfs_stage1_5       reiserfs_stage1_5
e2fs_stage1_5  menu.lst           stage1
fat_stage1_5   menu.lst~          stage2
walterp@VM1:/boot$ 

```

Please make sure you have these files present and accounted for.

OK, so now to try and ensure your boot loader is installed correctly.  I'm assuming you don't currently have anything on the secondary disk so I can wipe the partition table/mbr from that disk?  Only if so, then please firstly enter the following command:

```
sudo dd if=/dev/zero of=/dev/hdb bs=512 count=1

```

Be very careful to make sure the /dev/hdb is specified correctly, and the bs=512 and the count=1.  This effect of this command is to zero out the first sector (512 bytes) of the /dev/hdb device thereby removing the MBR and partition table.  This should avoid the secondary drive possibly causing trouble without us realising, by it perhaps containing GRUB as well or whatever.

Next, in a console enter:

```

walterp@VM1:/boot/grub$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd0,4)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,4)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> quit

walterp@VM1:/boot/grub$ 

```

Now at this point, if you have had all the above output, your machine *should* boot.  If it does not then there's some unknown voodoo going on with the hd names/config/ordering during boot.  Anyway, post back what you find.  Make sure you get exactly the same output as above, and post back any and all differences. Thanks for your patience.

---

### Post by bulldog on 2007-11-13
> **bumanie said:**
> Booted as per normal that time bulldog, that is with the 2nd hdd unplugged. Don't why it wouldn't do that last time I tried that anyway it did it this time.

You could boot from grub without any cd as it should be?

If this is yes,I would like you to disconnect this hdd and connect the second hdd [alone] and try to boot,I wonder if grub is present in the MBR.
You can't boot anything because the hdd is empty,but only to see if there's a trace of grub.

---

### Post by bumanie on 2007-11-13
> **bulldog said:**
> You could boot from grub without any cd as it should be?

That's correct.

---

### Post by bulldog on 2007-11-13
> **bumanie said:**
> That's correct.

Maybe you can look at my previous post? I edit again.

Sorry,ByteJuggler,can you hold on for a moment?
I apreciate your work but it's alittle distracting if we post all together
TY.

---

### Post by ByteJuggler on 2007-11-13
No problem.  I'll just suggest that given the above symptoms, doing the "dd" to nuke the secondary disk partitoin table might be a good idea to ensure it's not being picked as the default boot device by the BIOS (and if it has an old/Gutsy GRUB installed, then the Error 22 makes perfect sense...)  At least if you dd the secondary disk partition table then you'll get a very obvious boot failure when the secondary disk is reconnected and it is accidentally turns into the boot drive, which would then imply the BIOS drive boot ordering need changing, or the drive references need updating in the grub etc.  

Anyway I'll keep quiet for a bit. :KS

---

### Post by bumanie on 2007-11-13
I booted with the slave drive only enabled. Went through system check to the 'boot cd' point. It sat at that point and did nothing at all.

---

### Post by bulldog on 2007-11-13
> **ByteJuggler said:**
> No problem.  I'll just suggest that given the above symptoms, doing the "dd" to nuke the secondary disk partitoin table might be a good idea to ensure it's not being picked as the default boot device by the BIOS (and if it has an old/Gutsy GRUB installed, then the Error 22 makes perfect sense...)  At least if you dd the secondary disk partition table then you'll get a very obvious boot failure when the secondary disk is reconnected and it is accidentally turns into the boot drive, which would then imply the BIOS drive boot ordering need changing, or the drive references need updating in the grub etc.  

Anyway I'll keep quiet for a bit. :KS

Ty again,and you're perfectly right,read the postings I've made,how things should be setup.
But we're almost there,connecting the second drive should tell us if grub is installed on it.
If so,yes the boot order is wrong,which I stated allready in one of my previous postings.
But let us wait a while till TS report back to us.

---

### Post by bulldog on 2007-11-13
> **bumanie said:**
> I booted with the slave drive only enabled. Went through system check to the 'boot cd' point. It sat at that point and did nothing at all.
 No grub on that hdd,a bit disapointing I must say,well connect both hdd's and see how things go.
It shouldn't make a difference and your computer should boot without any error.

---

### Post by bumanie on 2007-11-13
> **bulldog said:**
> No grub on that hdd,a bit disapointing I must say,well connect both hdd's and see how things go.
It shouldn't make a difference and your computer should boot without any error.

Thanks a lot for your help and patience Bulldog. Very much appreciated.

---

### Post by bulldog on 2007-11-13
> **bumanie said:**
> Thanks a lot for your help and patience Bulldog. Very much appreciated.

No problem at all,if I can help someone,I certainly will do so.:)
Can you boot ubuntu with both hdd's connected?
I would like to know of things are solved :)

---

### Post by bumanie on 2007-11-13
Sorry bulldog, I went to sleep after it booted. I can confirm it boots with both drives connected. Thanks again.

---

### Post by jaybombalous on 2007-11-13
wtf did u do? I missed it... I was gonna suggest one last thing though. I don't know why but in my computer when I have a slave drive connected and set the jumper to 'cable select' gutsy gives me all kinds of fits. 

I dunno if this is an issue with my mother board or not, but I know something as simple as a freaking jumper can make your system do weird and not so wonderful things.

Glad to see u got it fixed.

---

### Post by bumanie on 2007-11-14
In the end to get the slave drive working properly, I followed the post of bytejuggler. I think the 'wiping' of the disk and reloading grub via --> root (hd0,4) --> setup (hd0) --> quit did the trick once the slave drive was clean.

---

