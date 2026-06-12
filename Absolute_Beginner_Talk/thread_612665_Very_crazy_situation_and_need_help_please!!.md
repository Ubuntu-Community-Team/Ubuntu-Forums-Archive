---
title: "Very crazy situation and need help please!!"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by Superdelphinus on 2007-11-14
This might be an interesting one for you to help me with!
After a failed unetbootin install i was left with a computer that went to a 'missing operating system' message. The dvd drive is broken so i can't use the recovery cd. Eventually i have managed to make a live  linux cd work from a usb stick and can boot into that (that took me 2 days to figure out!). When it has booted into the live cd version i can see the hard disks and everything is still in tact on them which means it must be a problem with XP actually booting rather than it being completely wiped off the drive. Any ideas how i can fiddle about with the windows files from within the live cd to make it boot again?

please help i feel so close and yet so far!

---

### Post by expatCM on 2007-11-14
so what you need to do is presumably reinstall Grub.  It is Ubuntu that you are trying to get going again and not Windows?

---

### Post by Superdelphinus on 2007-11-14
either would be great! Ideally i would just like to get windows booting again and then reinstall ubuntu from there (this live cd on the usb  is actually for linux mint)

---

### Post by expatCM on 2007-11-14
This thread may help but there are lots of others in a  similar light ...
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by Superdelphinus on 2007-11-14
Thanks that looks like it might help. If i was able to reinstall grub would it let me boot into windows? How do i know which partition is my boot partition in gparted?

---

### Post by expatCM on 2007-11-14
If Grub can detect the Window partition / boot sector then it may well add Windows to the boot menu.  No guarantees but it sounds like you have a reasonable hope that it will be straight forward.

In gparted you can usually guess your way through which partition is which.  For example you know that Windows will be formatted to either NTFS or FAT32, the Linux swap will probably be stated as that and the ext3 partition may well be your Ubuntu install.  It will depend on how you set up the computer in terms of partitioning and the number of drives and so on.

But read the linked thread a bit further ... you may not need to use gparted .....

---

### Post by Superdelphinus on 2007-11-14
Thanks for the pointers guys. The thing is i'm pretty new to all this partitions business. From gparted i can see that all the windows files are in Hda 1 and Hda 2 (because they are fat32). Basically i have 2 hard drives (although the system shows that i have one?) and one of them is formatted to fat32 and the other one (which has nothing on it) is NTFS. I also have two swap partitions for some reason rather than one

---

### Post by Superdelphinus on 2007-11-14
Hi would this help do you think (the bit under Using PCLinuxOS LiveCD and ms-sys to restore a standard MBR)

[http://docs.pclinuxos.com/Restoring_the_old_DOS/Windows_MBR](http://docs.pclinuxos.com/Restoring_the_old_DOS/Windows_MBR)

(sorry don't know how to do links

---

### Post by bulldog on 2007-11-14
You can boot into an OS,you can get to a terminal and you can type commands in it?

Well lets try to get some info here.
In a terminal```
sudo fdisk -l
``` small L not a one.
Can you post the output to the forum?

---

### Post by Superdelphinus on 2007-11-14
Hi thanks

I've had to go into work so i can't do that until later, sorry. I can boot using a usb stick version of a live cd so i'll post what happens later!

---

### Post by Superdelphinus on 2007-11-14
Hello, this is what the read out says:

mint@mint:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

it says invalid option - which one of these is most useful for you to know?

---

### Post by Superdelphinus on 2007-11-14
sorry i am an idiot! (misread a 1 for a l)

this is what it says:

mint@mint:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd5aed5ae

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         255     2048256   12  Compaq diagnostics
/dev/hda2             256        3764    28186042+   c  W95 FAT32 (LBA)
/dev/hda3            3765        5666    15277815    f  W95 Ext'd (LBA)
/dev/hda4            5667        7296    13092975   83  Linux
/dev/hda5            3765        4732     7775428+   7  HPFS/NTFS
/dev/hda6            5589        5666      626503+  82  Linux swap / Solaris
/dev/hda7   *        4733        5544     6522358+  83  Linux
/dev/hda8            5545        5588      353398+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 2048 MB, 2048901120 bytes
255 heads, 63 sectors/track, 249 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02258176

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         250     2000848+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(248, 254, 63) logical=(249, 24, 63)

---

### Post by bulldog on 2007-11-14
Some questions.
Did windows ever start up when placed in a logical partition?
Dis you put it there?
By my understanding this isn't possible,windows needs to boot from a primary.
Why are there two swap partitions?
You can safely delete one.
Then there is a message from sda1,but I don't know what it means.
We can try to reinstall grub into the MBR and see if we can get ubuntu to boot.
open a terminal and perform the next commands,read carefully what it says and keep looking for any error message.
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

Reboot and see if you can boot,that is if  there where no errors.

---

### Post by Superdelphinus on 2007-11-14
yes is the second post up there not the right output?

---

### Post by bulldog on 2007-11-14
> **Superdelphinus said:**
> yes is the second post up there not the right output?

?? what doe you mean?

---

### Post by Superdelphinus on 2007-11-14
ok failed at the first step - this is what i get:

grub> find /boot/grub/stage1

Error 15: File not found


ps - i don't actually have ubuntu installed on this system, only windows. But i don't know what files unetbootin left when it was busy messing everything up!

---

### Post by bulldog on 2007-11-14
> **Superdelphinus said:**
> ok failed at the first step - this is what i get:

grub> find /boot/grub/stage1

Error 15: File not found


ps - i don't actually have ubuntu installed on this system, only windows. But i don't know what files unetbootin left when it was busy messing everything up!

I have no idea what unetbootin is nor what it does.if there's only windows on that hdd,I'm very sceptical if it will boot,it shouldn't be in a logical partition.
If there is no linux installed is installing grub a little useless.
What is on hda7?

---

### Post by Superdelphinus on 2007-11-14
sorry what is a logical partition? how would windows have ended up there? Unetbootin is a way to install ubuntu without using a cd. that's what caused the problem in the first place - it got part way through and then crashed leaving me unable to boot. I'm not sure what's in hda 7 but i have been trying to install linux mint from this usb stick a couple of times and it got to 69% both times then failed so it could be the result of that! 

All i should really have on the hdd is windows xp! anything else could be deleted?

I don't know if this is important but although it says that it is one hdd of 60gb it shows up in file explorer as two hdds of 30gb each

---

### Post by bulldog on 2007-11-14
I see two hdd's hda and sda.[this could be the USB stick you're boot from]
hda is partitioned in a bit strange way,sda is empty with some vague message at the end.

I'm sorry to have to say this,but I don't think you can get windows to boot,first of all,it's on a place of the hdd,were it can't boot in my understanding.

If you boot this hdd,does it see your windows,will it start to boot and gives you an error,or is there nothing happening?

Device Boot Start End Blocks Id System
/dev/hda1 1 255 2048256 12 Compaq diagnostics  <-----   some recovery tool?
/dev/hda2 256 3764 28186042+ c W95 FAT32 (LBA)<--- no idea
/dev/hda3 3765 5666 15277815 f W95 Ext'd (LBA)<------extended partition
/dev/hda4 5667 7296 13092975 83 Linux<-----------------some sort of linux?
/dev/hda5 3765 4732 7775428+ 7 HPFS/NTFS<-----------windows I guess
/dev/hda6 5589 5666 626503+ 82 Linux swap / Solaris<--swap partition 1
/dev/hda7 * 4733 5544 6522358+ 83 Linux<----------------some sort of linux?
/dev/hda8 5545 5588 353398+ 82 Linux swap / Solaris<--swap partition 2

---

### Post by Superdelphinus on 2007-11-14
i think the sda might be the memory card that this is running from?
Right now i can see everything in the hard drive including all the windows files - it's very frustrating!
When i boot from the hard drive it just says missing operating system

---

### Post by bulldog on 2007-11-14
The only advice I can give is not a happy one.
I should backup the valuable data and start over again.:(
You need a windows install cd to recover this,and I'm not sure of this would work.

I can say use the system rescue cd or super grub or what ever,but without having a cd-rom device this is useless.
So basically,there are some things left to try,but you need a cd-rom device.

---

### Post by Superdelphinus on 2007-11-14
i assumed that the w95 fat32 was windows? I do know that windows is installed in the f32 formatted hdd1. hdd2 is formatted in ntfs (even though there is technically only one hdd)

to be honest i'm not bothered about losing windows as i have everything important backed up - it's just that whilst i'm without a dvd drive working it would've been nice to get it booting again without having to wait until i get an external drive to load the recovery disks from!

I'm still not clear how windows could've ended up in a place where it can't be booted from?

---

### Post by Superdelphinus on 2007-11-14
you mean there's a chance it's screwed even if i delete it and then load xp on again?

---

### Post by bulldog on 2007-11-14
In one of my previous post,I made an asumption what is on your hdd,I could be wrong in that ofcourse.
I thought the NTFS partition was windows,but now you say it's a FAT32 partition.

Never the less,without a cd-rom device to restore the windows bootloader and a windows install cd ,I can't do much I'm afraid.

---

### Post by Superdelphinus on 2007-11-14
no worries - you tried, cheers. I might try and install linux mint from the pendrive again and see if it does anything.

When i do the install if i choose guided write to whole disk will that wipe windows out completely (and everything else on the hdd)?

---

### Post by bulldog on 2007-11-14
> **Superdelphinus said:**
> you mean there's a chance it's screwed even if i delete it and then load xp on again?

Your current install could be recovered with the right tools.
The hardware isn't broken,just your windows is.
If you have a cd-rom device and the system rescue cd,you can probably restore your windows.
From there you can delete partitions you don't want to use.

I should prefer to clean the whole hdd,by deleting all the partitions.
Than create a 10GB partition for the /  [root] 
A 1-2 GB partition for swap
A /home as big as you want.
Then try to install your linux.

Your hdd is now a mess and this will not help the installer very much.
So clean up,make new partitions and install.

---

### Post by Niniel on 2007-11-14
Have you tried Windows boot disks (floppies)?
Just to restore the MBR, maybe that'll help.

---

### Post by bigken on 2007-11-14
you could try the win xp floppies if you have a floppie drive this will allow you to boot into a console and try things like fixmbr fixboot

[http://support.microsoft.com/kb/310994](http://support.microsoft.com/kb/310994)


good luck

---

### Post by barney385 on 2007-11-14
**UNetbootin**

UNetbootin allows for the installation of Ubuntu, and other distros.

UNetbootin uses a Windows or Linux-based installer to install a small modification to the bootloader (bootmgr and bcdedit on Vista, grldr and boot.ini for NT-based systems, grub.exe and config.sys for Win9x, or grub on Linux), uses the bootloader to boot the netboot initrd and kernel, then uses that to download and install Ubuntu directly from the internet, no CD required. After Linux is installed, the modification to the bootloader is then undone.


[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by Superdelphinus on 2007-11-14
no i don't have a floppy drive on this thing either! Really i just want to get a working OS on here now (i'm really not that bothered about windows at all at the moment!). I only use video editing stuff on xp and i won't be able to use any of that until i've got a new dvd player anyway so the saving of windows can wait.

Would it be possible for you guys to tell me which partitions i can safely delete from the readouts above now so that i can get this working from the hard drive rather than having to run a non persistant os for the next month or so!?

---

### Post by Superdelphinus on 2007-11-14
Guess what guys - you're not going to believe this!

I'm typing this from windows!!!!

All i did was change the flag of hda2 in gparted to 'boot' and rebooted and hey presto xp booted again!
Uninstalled unetbootin and here i am back at where i was 4 days ago!!

Any tips on how i can clean up the system ready to try the linux instillation again from here?

---

### Post by Niniel on 2007-11-16
Neat.

Now in order to prepare your system, you should delete all the partitions you don't need for Windows, and then install ubuntu from your live USB stick. You could then give the entire free space to Linux, minus a swap partition of 512MB - 1GB. 

> /dev/hda1 1 255 2048256 12 Compaq diagnostics
/dev/hda2 256 3764 28186042+ c W95 FAT32 (LBA)
/dev/hda3 3765 5666 15277815 f W95 Ext'd (LBA)
/dev/hda4 5667 7296 13092975 83 Linux
/dev/hda5 3765 4732 7775428+ 7 HPFS/NTFS
/dev/hda6 5589 5666 626503+ 82 Linux swap / Solaris
/dev/hda7 * 4733 5544 6522358+ 83 Linux
/dev/hda8 5545 5588 353398+ 82 Linux swap / Solaris

That would be hda4, hda6, hda7 and hda8. 
Depending on where XP is installed, and where your applications and your personal files reside, you may also be able to delete hda2, hda3 or hda5.
Hda1 seems to be a so-called rescue-partition. You may want to hang on to that for now.

Maybe it's best if you deleted the partitions from within Windows, then you can see what partitions/drives you use for XP and you can clean one or two out so that you can get rid of them as well. Hda2 could be your boot drive though so if it has a file called "ntldr" on it, keep it. 

-> Control Panel/Admin Tools/Computer Management/Storage/Disk Management.

---

### Post by ukripper on 2007-11-16
> **Superdelphinus said:**
> Guess what guys - you're not going to believe this!

I'm typing this from windows!!!!

All i did was change the flag of hda2 in gparted to 'boot' and rebooted and hey presto xp booted again!
Uninstalled unetbootin and here i am back at where i was 4 days ago!!

Any tips on how i can clean up the system ready to try the linux instillation again from here?

This may help [http://digitalgraphy.wordpress.com/2007/10/20/dual-booting-ubuntu-710-gutsy-gibbon-and-windows-ntxpvista/](http://digitalgraphy.wordpress.com/2007/10/20/dual-booting-ubuntu-710-gutsy-gibbon-and-windows-ntxpvista/)

---

