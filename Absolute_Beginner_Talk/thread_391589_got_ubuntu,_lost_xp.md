---
title: "got ubuntu, lost xp"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by owlz on 2007-03-23
hi im new to ubuntu and baisically linux. i have recently got a live cd and booted it up but not installed it just to see what it is like. it crashed so i had to hold down the power button to turn it off as you do and booted it back up into ubuntu from the live cd because it was still in the drive and i turned it off and took out the disc like it says and tried re-booting back into windows xp but all i got was a black screen saying disk read error occured press ctrl+alt+delete to restart but that didnt work. it boots up ubuntu perfectly if i put the disc in but it wont let me get onto xp any help greatly appreciated.

P.S i havent got a xp disc because im using a laptop that came with xp already installed and i havent got a floppy drive

---

### Post by mahy on 2007-03-23
> **owlz said:**
> P.S i havent got a xp disc because im using a laptop that came with xp already installed and i havent got a floppy drive

If you don't have an original xp disc, then you have to get another one somehow. Or you can hand it over to the tech support, if you're clueless.

---

### Post by igknighted on 2007-03-23
> **owlz said:**
> hi im new to ubuntu and baisically linux. i have recently got a live cd and booted it up but not installed it just to see what it is like. it crashed so i had to hold down the power button to turn it off as you do and booted it back up into ubuntu from the live cd because it was still in the drive and i turned it off and took out the disc like it says and tried re-booting back into windows xp but all i got was a black screen saying disk read error occured press ctrl+alt+delete to restart but that didnt work. it boots up ubuntu perfectly if i put the disc in but it wont let me get onto xp any help greatly appreciated.

P.S i havent got a xp disc because im using a laptop that came with xp already installed and i havent got a floppy drive

When you boot the live CD, can you mount the windows drive and see if the data is still there?  Also, can you go into your bios to set it to boot to winXP and not to CD or floppy first?

---

### Post by owlz on 2007-03-23
i cant get into the system because its "locked in a virtual vault" because i havent installed it.

---

### Post by doobit on 2007-03-23
> **owlz said:**
> i cant get into the system because its "locked in a virtual vault" because i havent installed it.

What do you mean by that?

---

### Post by owlz on 2007-03-23
if you boot it from the cd then you cant access your hard drive and i dont know how to mount it. sorry for lack of knowledge, i havent had to mount any hard drive before
(im only 13)

---

### Post by letitsnow on 2007-03-23
so you broke your parents computer :p , that was my first experience with ubuntu as well.

go into terminal and type:
```
sudo fdisk -l
```

---

### Post by owlz on 2007-03-23
nah its not my parents computer its my laptop. im the best in my school in computers lol

---

### Post by owlz on 2007-03-23
i entered the command into a terminal and it came up with ```
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         563        4863    34547782+   7  HPFS/NTFS
/dev/sda2               1         536     4305388+  41  PPC PReP Boot

Partition table entries are not in disk order

Disk /dev/sdb: 1014 MB, 1014497280 bytes
17 heads, 32 sectors/track, 3642 cylinders
Units = cylinders of 544 * 512 = 278528 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3643      990704    b  W95 FAT32

```

---

### Post by Z_Klein on 2007-03-23
It seems like your computer is trying to boot from the CD automatically, even though there is no CD in the drive. That's what causes the error. All your stuff is still there, so no need to use PC recovery or anything. Here's what you can do:

1). At the very beginning of your computer's startup, you know how there's that screen that has the logo of the company that made it (Dell, HP, Gateway, etc...)? Well, when that shows up, find the key to select where to boot from (for HP, it's f1), and hold it down at that screen. Then, it should show a menu with a few different places. Select the hard drive (or partition) that has Windows XP on it, and hit "Enter". That should boot your computer into Windows. 

If this doesn't work, just say so.

---

### Post by owlz on 2007-03-23
ive tried doing that but when i try to boot from the hard drive it just gives a black screen and a flashing underscore

---

### Post by camz on 2007-03-23
Ok dude you seem very similar to me. I installed it on my rubbish laptop and I'm also 13. I currently run Ubuntu and WinXP, and while being the best in my school, I'm also better than my dad's computer programmer friend, although you will still see a lot of my posts asking for help on the forum. Here's my opinion, you don't have to listen.. Forget XP, install Ubuntu from your Live CD, and stick with it. At a later date you can re-install XP if really needed.

Camz

---

### Post by owlz on 2007-03-23
i would but ive got a lot of important docs wich i can only access from xp plus it wont let me install ubuntu, ive tried countless amouts of times but no luck. so i need to get on to xp first then get all of my documents then install ubuntu. that is what i was planning on in the first place

---

### Post by Z_Klein on 2007-03-23
> **owlz said:**
> ive tried doing that but when i try to boot from the hard drive it just gives a black screen and a flashing underscore

Are you booting from the right hard drive/partition? If you boot from the hard drive that **doesnt** have your bootloader (GRUB, or whatever you have), won't load, and it will give that screen. 

I had the same problem when I first installed Fedora Core. I tried to boot from my second hard drive (the one with Fedora), and it would give me that black screen with a while inderscore.

---

### Post by dstew on 2007-03-23
Dear owlz:

It looks like you have a PPC PrEP system. This is a type of bios + special partition that boots the system. I think you need to boot the PPC PrEP partition and not the NTFS partition as you are perhaps trying to do. I do not know a lot about the PPC PrEP system, but I will look into it for you. In the meantime, try to boot the PPC PrEP partition.

---

### Post by owlz on 2007-03-23
it is an emachines laptop with intel celeron M420 1.6GHz and that thing you suggested with the f1 stuff but the key for this machine is f11 so when i use that it comes up with a blue box and 3 options: S-ATA hard drive, CD-R/CD-RW/DVD-RW or network: realtek

---

### Post by camz on 2007-03-23
Didn't you back up your files? Also, I'm not sure how, but if you are sure that XP is still there, just not accessible, you could mount the partition from Ubuntu and extract the files.

---

### Post by dstew on 2007-03-23
Here is more on the PPC PrEP stuff, in a thread about using Power PC linux. I know you do not have a Power PC processor, but the thread explains how a PPC bios works with the PPC PrEP partition. Basically, the BIOS will always boot the PPC PrEP partition, so the linux booter has to be there.

[http://penguinppc.org/~hollisb/linux/carolina/](http://penguinppc.org/~hollisb/linux/carolina/)

---

### Post by owlz on 2007-03-23
i was going to back up my files but the program wouldnt work so i thought stuff it ill try it once and then back up my files if i liked it and i wanted it installing but unlucky me this had to happen! and how could i mount the drive and extect the files because ive tried ```
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
``` and i dont know where i went wrong.

---

### Post by tcrroadie on 2007-03-23
Sounds like the Windows boot loader is borked.  One thing to keep in mind about your BIOS settings on your laptop is that when you select your hard drive as your boot device, it doesn't matter what partition Windows XP is on, the BIOS looks for the Windows boot loader in the first sector of the hard drive (mbr).

I believe you will need to locate a Windows installation disc in order to repair you mbr (master boot record).  This also assumes that the data on your Windows partition is not also corrupted.

---

### Post by tcrroadie on 2007-03-23
> **owlz said:**
> i was going to back up my files but the program wouldnt work so i thought stuff it ill try it once and then back up my files if i liked it and i wanted it installing but unlucky me this had to happen! and how could i mount the drive and extect the files because ive tried ```
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
``` and i dont know where i went wrong.

Your notebook has a serial ata drive. 

Try sda1.  This is the partition your Windows installation is on.

```
sudo mkdir /media/windows
sudo mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

---

### Post by owlz on 2007-03-23
i dont know where to get one. any suggestions? i dont want to pay excessive amounts of money. i dont know any one who has one

---

### Post by owlz on 2007-03-23
> **tcrroadie said:**
> 
```
sudo mkdir /media/windows
sudo mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

i have tried that and i get this error message ```
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by tcrroadie on 2007-03-23
I'm sorry, I'm at work on a Windows box at the moment and I can't remember the correct options to mount a ntfs partiotion.  

Try this.  This is from memory.  May be incorrect. 

```
sudo mkdir /media/windows
sudo mount /dev/sda1 /media/windows/  ntfs   0  0  
```

Another option for you is just install Ubuntu on your notebook pc.  You can resize the partition that Windows XP is on, to make room for an additional partition for Ubuntu.  Then install Ubuntu to your new extra partition and tell the Ubuntu installer to install Grub to the mbr (master boot record).  

Then you can edit your grub file to include your Windows partition and you should be able to boot Windows with Grub. I can tell you what to add to your grub file to boot Windows, it is very easy.  This also assumes that your Windows installation is not heavily fragmented.  You can just create a small 8-10 gig partition for your Ubuntu installation.

---

### Post by owlz on 2007-03-23
i have just tried that and i have got this message: ```
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

```

---

### Post by camz on 2007-03-23
I can't remember when I did it but you have to edit something there.

---

### Post by owlz on 2007-03-23
do you think that if i bought a floppy drive and made a windows startup disk on my other pc then used that would it work? please try and remember the thing you have to edit first though

---

### Post by tcrroadie on 2007-03-23
Try mounting your windows partition with this, after creating your /media/windows directory of course.

```
sudo mount /dev/sda1 /media/windows -t ntfs -o nls=utf8,umask=007,gid=46
```

If that doesn't work try changing the filesystem type to hpfs.  
```

sudo mount /dev/sda1 /media/windows/ -t hpfs -o nls=utf8,umask=0222
```

> do you think that if i bought a floppy drive and made a windows startup disk on my other pc then used that would it work? please try and remember the thing you have to edit first though

I believe as long as you can set your laptop to boot from a usb device, it should work.

---

### Post by dstew on 2007-03-23
tcrroadie said:

> One thing to keep in mind about your BIOS settings on your laptop is that when you select your hard drive as your boot device, it doesn't matter what partition Windows XP is on, the BIOS looks for the Windows boot loader in the first sector of the hard drive (mbr).

This might not be true for a PPC PReP bios (or firmware).

> When it boots, the firmware on all PReP machines looks for partition of type "PReP Boot" (type 0x41) on your hard drives. Once it finds it, it boots from it, so the idea is to 'dd' a Linux kernel (zImage) there. The partition is usually created as 5 MB to allow room for growth. Due to firmware limitations, do not make the boot partition larger than 8 MB.

This is from another Linux Power PC page. I know he does not have a Power PC, but he may have a PReP firmware boot setup.

---

### Post by owlz on 2007-03-24
> **tcrroadie said:**
> 

```
sudo mount /dev/sda1 /media/windows -t ntfs -o nls=utf8,umask=007,gid=46
```

if i try that i get the error message: ```
mount: special device dev/sda1 does not exist

```


> 
```

sudo mount /dev/sda1 /media/windows/ -t hpfs -o nls=utf8,umask=0222
```


when i try this one i get this message: ```
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by chrismcollins on 2007-04-12
Hello,
I have the exact same problem and I was wondering if the same fix would work for me? when I type in sudo fdisk -l i get:

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3442    27647833+   7  HPFS/NTFS
/dev/hda2            3443        3952     4096575   83  Linux
/dev/hda3            3953        4016      514080   82  Linux swap / Solaris
/dev/hda4            4017        4864     6811560   83  Linux

Can i still access windows? or am I screwed?

---

