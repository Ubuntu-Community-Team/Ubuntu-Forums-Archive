---
title: "windows xp"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by faranell on 2008-02-05
hello,

i have a problem with getting back to windows xp on my dell, i had the live-cd from ubuntu 7.10 and installed it. After some time i though i have to go back to windows xp and play WoW... but now the problem is i cant go back :confused: i changed the /boot/grub/menu.lst but it says: invalid device requested. after trying hours i though lets try norton ghost 10 by using cd boot (at the restart of your comp) didnt worked too.. now my question is what can i do about it since i dont have a windows xp iso because u dont get it from dell.

faranell

---

### Post by Hokum15 on 2008-02-05
Have you made sure you can still see your NTFS partition on the hard drive? If so try just taking grub out of the boot.ini and see if that works?

---

### Post by buzzmandt on 2008-02-05
hate to be the bearer of bad news, but it sounds as though win xp is no longer on your machine.  A dual boot set up automatically sets up a boot option for xp, if it doesn't then you had to have selected the wrong option and deleted your win xp system.

---

### Post by PmDematagoda on 2008-02-05
Post the outputs of:-
```
cat /boot/grub/menu.lst
```
and
```
sudo fdisk -l
```

---

### Post by bumanie on 2008-02-05
Please type in terminal
> sudo fdisk -lu --> enter, give password
and post the output

---

### Post by emarkd on 2008-02-05
Sounds like an error in your menu.lst file.  Could you post the output of:

```
sudo fdisk -l
```

and

```
cat /boot/grub/menu.lst
```

---

### Post by faranell on 2008-02-05
sudo fdisk -lu says:

Schijf /dev/sda: 80.0 GB, 80060424192 bytes
255 koppen, 63 sectoren/spoor, 9733 cilinders, totaal 156368016 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Schijf-ID: 0x434e78fe

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *          63   150304139    75152038+  83  Linux
/dev/sda2       150304140   156360644     3028252+   5  Uitgebreid
/dev/sda5       150304203   156360644     3028221   82  Linux wisselgeheugen

Schijf /dev/sdb: 250.0 GB, 250059350016 bytes
255 koppen, 63 sectoren/spoor, 30401 cilinders, totaal 488397168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Schijf-ID: 0x0359cc01

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1   *          63   488392064   244196001    7  HPFS/NTFS

sudo fdisk -l says:

Schijf /dev/sda: 80.0 GB, 80060424192 bytes
255 koppen, 63 sectoren/spoor, 9733 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x434e78fe

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *           1        9356    75152038+  83  Linux
/dev/sda2            9357        9733     3028252+   5  Uitgebreid
/dev/sda5            9357        9733     3028221   82  Linux wisselgeheugen

Schijf /dev/sdb: 250.0 GB, 250059350016 bytes
255 koppen, 63 sectoren/spoor, 30401 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x0359cc01

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS

cat /boot/grub/menu.lst says:

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=3e42c685-f314-4052-9f92-961954cbbb69 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3e42c685-f314-4052-9f92-961954cbbb69 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3e42c685-f314-4052-9f92-961954cbbb69 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

title           Windows 95/98/NT/2000
root            (hd0,1)
makeactive
chainloader     +1

btw i have only 1 partition, and thank you all for the quick reactions :)

---

### Post by PmDematagoda on 2008-02-05
Change the "root" line of the entry created for Windows from:-
```
root (hd**0,1**)
```
to
```
root (hd**1,0**)
```
and then try booting Windows.

---

### Post by faranell on 2008-02-05
did it still nothing :(

---

### Post by hyper_ch on 2008-02-05
what error?

---

### Post by faranell on 2008-02-05
it says: error 12: invalid device requested

---

### Post by faranell on 2008-02-05
what can i do about this? is the only option to download a xp,iso? or is it still possible to go to XP?

thanks faranell

---

### Post by bumanie on 2008-02-05
Firstly, can you please check your bios to make sure both your hard drives are recognised and set to boot in the correct order.
Secondly, can you confirm that you have linux on your first drive and windows on your second drive.

---

### Post by Desperate on 2008-02-05
Can you still mount /dev/sdb1 ? so you can safe your data and burn it to disk?
I'm just before installing Ubuntu and you are having the nightmare I fear I'll have too when I try it, so I would like to follow this closely to gain some confidence, before I dive in :)
I wrecked my hard disks but after mounting it in Ubuntu I was able to access it again.

---

### Post by rkd on 2008-02-05
Was Windows on the first (or only) hard drive before you installed Ubuntu?

If yes, did you move the drive containing Windows to be the second hard drive, then install Ubuntu onto the new first hard drive?

Or is the history somewhat different?  If different, give us a sketch of the history.

---

### Post by faranell on 2008-02-06
**at bumanie:**

i only got 1 hard drive so i think he will recognis this one (else i even couldnt get to unbuntu?)
im not sure but i think ubuntu made a visual second partition (z: ) (dont know that for sure)

**at desperate:**

i only got a sda sda1 sda2 and sda5 no sdb1 :(

**at rkd:**

yep windows was on my only and first hard drive (c: )
no i think ubuntu made a (z: ) drive were he putted all his stuff (but im not sure about it)

i will in the couple of hours try to **not** install ubuntu on my other computer which has got vista and then i will tell you all the things i did on the live-cd install.

---

### Post by faranell on 2008-02-06
also the strange thing is i installed wow on ubuntu and the map that its in is windows applications --> programs --> world of warcraft also notepad is in the same folder :confused:

i also see now that when i check /home/jeroen/.wine/drive_c there is still the map ¨program files¨ and ¨windows¨ so i have a good feeling that windows xp is still on the machine :)

---

### Post by GSF1200S on 2008-02-06
> **faranell said:**
> also the strange thing is i installed wow on ubuntu and the map that its in is windows applications --> programs --> world of warcraft also notepad is in the same folder :confused:

i also see now that when i check /home/jeroen/.wine/drive_c there is still the map ¨program files¨ and ¨windows¨ so i have a good feeling that windows xp is still on the machine :)

No, thats wines way of simulating the Windows layout (need techie to be more proper here). For example, Wine links My Documents to /home, etc... The reason WoW is in the folder with notepad is that they are both Wine applications...

I would be patient here.. the windows partition is listed in the results of fdisk -l, so its in there. Im no master with grub so Ill wait for a more informed response to come along...

Good Luck!

---

### Post by faranell on 2008-02-06
ok the first thing i had to in the welcome menu was to set the language in Dutch when i did that, the installer came with the timer which is Amsterdam for me (next) then he came with the keyboard selection which for me was the US international (next) then he came with a prepare disk space which has 3 options:

- guided resize SCI1 (0,0,0) partition #1 (sda) and use freed space
- guided use entire disk
- manual

here i choose guided resize SCI1

after hitting next he was installing something and after that he ask me my name/user/password and computer name when i hit next he gave me a overview of this (this is the last menu he gave me) when i hit install he will install ubuntu.

this is what i did on the live-cd installation, i hope you have enough information now what i did :)

---

### Post by faranell on 2008-02-06
> **GSF1200S said:**
> No, thats wines way of simulating the Windows layout (need techie to be more proper here). For example, Wine links My Documents to /home, etc... The reason WoW is in the folder with notepad is that they are both Wine applications...

I would be patient here.. the windows partition is listed in the results of fdisk -l, so its in there. Im no master with grub so Ill wait for a more informed response to come along...

Good Luck!

i installed wow with crossover but since it is from the same group that made wine, i suppose its the same ^^

---

### Post by SteveHillier on 2008-02-06
> **faranell said:**
>  now my question is what can i do about it since i dont have a windows xp iso because u dont get it from dell.

faranell

I want only to comment on this part of your original post.
If you do have to reinstall windows you should be able to install from a borrowed windows disk from what ever source.  If you know someone who has another Dell like yours ask them if they have the recovery disks.
Two things to make sure of.
1.  Make sure you install the same version of XP as your original ie Home or Professional.
2.  During the install use the 25 digit product code that came with your machine - you should find a sticker on your machine somewhere.  You will probably need to activate the product again and this code is important.  Whatever you do, do not use the product code from the borrowed disk - you will invalidate the activation.
Please remember if you do this that you will clean everything off the hard disk, including any Ubuntu files.

This is not for the faint hearted!!
Good luck

---

### Post by faranell on 2008-02-06
ok damn.. i think im in real ****, i could get norton ghost 10 running by CD boot in BIOS. but when i want to restore my old c: drive there aint one :confused: (well there is but its my extern disc) there is a z: drive which is 3 mb :confused: and the name is MS-RAM or something like that and there is a x: drive which is my CD player.. there aint an ubuntu partition that i can see :mad: how is this possible? now im really confused :confused:

---

### Post by Desperate on 2008-02-06
> **faranell said:**
> 
**at desperate:**

i only got a sda sda1 sda2 and sda5 no sdb1 :(



But you list 

 sudo fdisk -lu says:
 blabla and then
Apparaat Opstart Begin Einde Blokken ID Systeem
/dev/sdb1 * 1 30401 244196001 7 HPFS/NTFS

Now I'm wondering

---

### Post by bumanie on 2008-02-06
Your fdisk -l says that there is two hard drives, sda and sdb, but you say there is only one hard drive. If there was only one hard drive you would have sda drive only (as far as I know) with it various partitions, there should not bee a sdb drive, unless grub has got totally confused.
Could you post output of > sudo blkid and the output of > gksudo gedit /boot/grub/device.map

---

### Post by faranell on 2008-02-06
**sudo blkid says:**

/dev/sda1: UUID="3e42c685-f314-4052-9f92-961954cbbb69" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="ce7b6007-5120-4f32-87d3-cc77f084e3db" 

**gksudo gedit /boot/grub/device.map says:**

(hd0)	/dev/sda

---

### Post by bumanie on 2008-02-06
OK, that certainly shows that there is only one hard drive. Can't understand why fdisk -lu displays an entry labeled sdb1 - very strange. Going back to fdisk -lu what is on the sda2 partition? 
/dev/sda2 150304140 156360644 3028252+ 5 Uitgebreid

---

### Post by MariusSilverwolf on 2008-02-06
> **faranell said:**
> i dont have a windows xp iso because u dont get it from dell.l

Dell, by default shipping standards, includes a packet with every system that includes a Windows CD, an Applications CD, driver CDs, and various user manuals related to the equipment.  If you ordered this system directly from Dell and it did not come with this packet, call them.  They will need your model and serial numbers to confirm the version of the disk they need to ship.  If they cannot provide you the disk, you could try calling Microsoft.  Those are the only two companies that can provide you with a legal Windows disk.

---

### Post by Tatty on 2008-02-06
> **MariusSilverwolf said:**
> Dell, by default shipping standards, includes a packet with every system that includes a Windows CD, an Applications CD, driver CDs, and various user manuals related to the equipment.  If you ordered this system directly from Dell and it did not come with this packet, call them.  They will need your model and serial numbers to confirm the version of the disk they need to ship.  If they cannot provide you the disk, you could try calling Microsoft.  Those are the only two companies that can provide you with a legal Windows disk.

Are you sure? 

I thought that as long as you have a legal license for windows (the product key sticker on the side of the machine) then it doesnt matter where you got the CD from.  As long as you use your own product key to activate it...

---

### Post by MariusSilverwolf on 2008-02-06
> **Tatty said:**
> Are you sure? 

I thought that as long as you have a legal license for windows (the product key sticker on the side of the machine) then it doesnt matter where you got the CD from.  As long as you use your own product key to activate it...

Microsoft is rather particular about the source of the disk as well as the product key.  Dell, typically, does not attach the product key to the side or back of the machine, though, instead including it in the package containing the other disks and manuals.  The Dell OEM Windows CD typically makes no call for the Product Key, instead having it embedded, whereas a standard retail version will make that call.  Without the aforementioned packet, that key cannot be found.

Windows trickiness.  Not pleasant.

---

### Post by NeoGreen on 2008-02-06
I have always installed with any copy, I just make sure it is Professional or Home and either Service Pack 1 or 2.

---

### Post by faranell on 2008-02-07
> **bumanie said:**
> OK, that certainly shows that there is only one hard drive. Can't understand why fdisk -lu displays an entry labeled sdb1 - very strange. Going back to fdisk -lu what is on the sda2 partition? 
/dev/sda2 150304140 156360644 3028252+ 5 Uitgebreid

hehe how can i check this? im just a new linux user so i dont know that much about it :P

---

### Post by rkd on 2008-02-07
It appears to me that sda2 is the extended partition within which sda5 was created. Notice that the start and end addresses for sda2 and sda5 overlap, and notice that the ID of sda2 is 5.

Apparaat Opstart Begin Einde Blokken ID Systeem
/dev/sda1 * 63 150304139 75152038+ 83 Linux
/dev/sda2 150304140 156360644 3028252+ 5 Uitgebreid
/dev/sda5 150304203 156360644 3028221 82 Linux wisselgeheugen

In post #22, you mentioned an external disk. Perhaps that is the sdb that was listed in the fdisk -l output you showed us in post #7. Do you have a 250 GB external disk with one Windows partition covering the whole disk? Could it be that this disk was connected to the computer when you did the fdisk -l command you showed in post #7?

I will assume, for a moment, that there is a 250 GB external disk. What do you use that disk for? I hope it is a backup of your Windows files.

As far as I can tell, there are no Windows files on the 80 GB disk (sda) any more. About 75 GB is allocated to a Linux data partition and about 3 GB are allocated to a swap partition. When you installed Ubuntu from the Live CD, it appears that you accidentally told it to use the whole disk for Ubuntu.

When you tried to restore using Ghost, I think it was correct to tell you there was no C: partition to restore into -- it is gone. I don't know much about Ghost, but it could be that Ghost does not know anything about Linux partitions and so would not tell you anything about the Linux data partition on the drive. The z: drive it showed probably was the swap partition (was it 3 GB rather than 3 MB?). MS-RAM might be a term Ghost uses for swap partitions. As I said, I don't know much about Ghost.

So my suggestion is that you think about my guesses here, check them as much as you can, then post here again either to tell us what you believe your disks now contain, or to ask us more questions to help you determine what is on your disks.

If you were using Ghost to make complete backups of your Windows partition on the 80 GB disk, then I think it is likely that you would be able to recover your most recent backup. I believe you would have to wipe out the Ubuntu installation in order to do that recovery. If there are any files on the Ubuntu system that you want to save, you could back them up before wiping out Ubuntu. Once you have recovered your Windows from the external disk, you could install Ubuntu again, taking care to tell it to share the disk with Windows.

If you do not have a complete backup of your Windows partition, then you may have a problem. If there were some files in Windows that you don't have backed up, it will be very hard to recover them, or maybe impossible.  Don't panic, though. If there were very important files for which you do not have backups, stop using that computer until you have gotten some advice from us about how to preserve as much as is still there.

If you do not have a complete backup of the Windows partition, but it did not hold any files that you need to recover, then you should be able to put the computer back to its factory-shipped state using whatever recovery CDs Dell supplied with the computer.

So over to you -- tell us how much of my guesses are correct, tell us as much as you can determine about what is on the disks now, and tell us what direction you want to go in.

---

