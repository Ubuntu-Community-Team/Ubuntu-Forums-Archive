---
title: "How to bypass the 4-partitions limit?"
date: 2008-05-05
forum: Apple Hardware Users
---

### Post by MarcelloSav on 2008-05-05
Hello guys,
I have got a MacBook with MacOS and Ubuntu 7.10 .
Now, since I had problems with upgrade to 8.04, I'd like to separate home and root partitions, but I know that there is a limit of 4 partitions.
I obviously have one partition for Efi, one partition for MacOS, one for Linux and one for swap.
Now, is there a way for bypassing this limit?

Thanks for your replies and forgive my bad english.

Marcello.

---

### Post by chewearn on 2008-05-05
Create an extended partition, install the linux inside it.  You can create a large number of logical partitions inside an extended partition (not sure the limit, but definitely more than you will ever need).

---

### Post by MarcelloSav on 2008-05-05
Ok thanks!
I have another little question, but I think that it's better to go OT here instead of opening another thread...
Is my actual 32-bit home compatible with the 64-bit Ubuntu?

---

### Post by az on 2008-05-05
> **MarcelloSav said:**
> Hello guys,
I have got a MacBook with MacOS and Ubuntu 7.10 .
Now, since I had problems with upgrade to 8.04, I'd like to separate home and root partitions, but I know that there is a limit of 4 partitions.


Does a MacBook use a dos partition table with the 4 primary partition limit or does it use a mac partition table?

> **MarcelloSav said:**
> Ok thanks!

Is my actual 32-bit home compatible with the 64-bit Ubuntu?

Since it's only configuration files, it should be.

---

### Post by aikiwolfie on 2008-05-05
I think Ubuntu installs the appropriate kernel automatically.

---

### Post by cyberdork33 on 2008-05-05
Macs do not have the ability to create extended / logical partitions. They have a GPT formatted disc which actually allows for a very large number of partitions beyond 4 and does not require anything like that.

However, the 4 partition "limit" is a limitation of the emulated MBR partition table and is always the first 4 partitions in your GPT. The problem is that you have incorrectly assumed that you can only use those first 4 partitions. It is only required that the partition containing the bootloader is installed in one of the first 4 partitions as well as windows, and any partitions that you want windows to be able to access. Other partitions have no issues being beyond #4. (This actually includes OSX itself.)

basically... create your root partition as one of the first 4, and you can put the swap and home partitions wherever you like and they will work fine. (Once the kernel is loaded, Linux can access the GPT and see all the partitions on the disc.)

---

### Post by MarcelloSav on 2008-05-05
So if I split the actual linux partition in two, my swap partition will be the last partition, #5, I will not have any kind of problem?

---

### Post by flaggh on 2008-05-05
> **MarcelloSav said:**
> So if I split the actual linux partition in two, my swap partition will be the last partition, #5, I will not have any kind of problem?

I would not bother with a swap partition.  A swap file on your root partition will be just as effective.  Read the Swap FAQ for more information and instructions on creating a swap file:
[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by MarcelloSav on 2008-05-05
> **flaggh said:**
> I would not bother with a swap partition.  A swap file on your root partition will be just as effective.  Read the Swap FAQ for more information and instructions on creating a swap file:
[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

Oh it's really interesting! I didn't know that... But since there is no problem in creating a new partition, deleting the swap partition right now is useless for me. Thanks for the news. ;)

---

### Post by cyberdork33 on 2008-05-05
> **MarcelloSav said:**
> So if I split the actual linux partition in two, my swap partition will be the last partition, #5, I will not have any kind of problem?
nope.

---

### Post by kuadhual on 2008-05-06
I just want to share my experience (pardon my engrish). I got hint from many other site that most of it I cannot remember. 

I tried installing dual-boot osx and ubuntu, after a couple of osx re-install and more  ubuntu re-install, I think I got partition layout that will survive the next ubuntu release re-install. I got 9 partition in total, I put the /boot partition in front of Mac OSX partition. I'm using MacBook 4.1 SantaRosa and Leopard

This is what I did, your setup maybe different. ( Please don't follow this step, this is just a sharing, not a tutorial   :p ) :
[LIST]
[*]Boot using linux liveCD, I'm using GParted liveCD. OSX Disk Utility can't create anything smaller than 1GB 
[*]Delete macosx partition (partition 2, if the macbook is new or still in the original state), leave partition 1 (EFI partition, it's the FAT32 in the first partition) (OR you could just resize from OSX, I like clean install better)
[*]Plan the partition layout; mine is:

[LIST=1]
[*]EFI --> it's already there (around 200 MB)
[*]/boot partition for ubuntu (mine is 100MB) (macbook is using GUID partition table, not MBR. EFI can only boot from the first 4 partition. Linux has support for GUID, as long as the kernel booted)
[*]MacOSX System  partition (mine is 40GB)
[*]MacOSX Data partition (again, this is a GUID disk, there is no extended partition) (mine is 16GB) 
[*]MacOSX and Ubuntu shared partition (mine is 40GB)
[*]Swap file for ubuntu (I got 4GB of ram, I create 4,5GB for this)
[*]/ (root) (16 GB)
[*]/home (16 GB)
[*]/other (the rest) 
[/LIST]

[*]create  partition 2 - 9 from above _AS AN EMPTY PARTITION_
[*]reboot using mac OSX install DVD, install Mac OS X (I'm using leopard) to the 1st partition (the 2nd partition (the 40GB partition) in gparted, the EFI partition is hidden in Mac OSX) , don't install what you don't need (I deselect printer driver and language)
[*]Boot into OSX, using Disk Utility, format the 2nd (16 GB) as an Apple OSX partition (HFS+) journaled and the 3rd partition (40GB) as _CaseSensitive, Non-Journaled_ (HFSX), and leave the rest unformated. (read [this]("http://www.castyour.net/node/40") and [this]("http://ubuntuforums.org/archive/index.php/t-486483.html"))
[*]Update MacOSX and install [rEFIt]("http://refit.sourceforge.net/") in MacOSX
[*]Insert Ubuntu CD (I use alternate i386 CD and did command-line install) and reboot, Choose Linux CD from rEFIt menu
[*]Install ubuntu as usual, using partition 2 as /boot, 7 as / (root), 8 as /home and 9 as /data. Don't forget to name the partition (it's different from label) . (I notice that the HFS partition created from OSX has around 132 MB of free-space between partitions. Anybody know why?)
[*]After ubuntu installation has finish, restart and choose 'Start Partitioning Tool' from rEFIt menu, or you won't be able to boot to ubuntu. Sync GUID and MBR table. Every time you did something to a partition (format, delete, resize, etc), you have to resync again  
[*]Did whatever you used to do, from here on it's just the same as regular install
[/LIST]

I hope someone found an easier way to do this. I'm still tweaking my MacBook... trying to get the wireless working. ](*,)

---

### Post by cyberdork33 on 2008-05-06
> **kuadhual said:**
> I notice that the HFS partition created from OSX has around 132 MB of free-space between partitions. Anybody know why?
Disk Utility does that for some reason. There is a live cd out there called parted magic that is capable of creating (not resizing, well not growing anyway) HFS+ partitions. That should not leave the large spaces between partitions.

There probably is not really an easier way to do what you want, you just have a quite complicated partition scheme. I do want to point out a technicality... EFI is perfectly capable of booting from partitions other than the four in your MBR... "legacy" loaders rely on the MBR table and thus have to be in the first four partitions. At one time I had a setup with OSX on partition 6 and it worked fine there. Another user here (billbear) has also stated that you can have your Linux boot partition out beyond 4, but grub has to be installed on one of the first four partitions. There is nothing wrong with what you have done though, and I would have probably done similar.

---

### Post by benanzo on 2008-05-06
Just to throw another angle into the mix here, I was booting Windows XP, Mac OS X and Ubuntu off a pure MBR disk (no GPT at all) for quite awhile and it worked great.  It's quite involved and over-complicated but definitely doable.  I just used GRUB as the global bootloader rather than refit.  Basically it boils down to installing OS X like normal, then booting a live disc and making the installation into a tarball on an external disk, changing the partition scheme, then untarring OS X back onto it's partition.  This allows for the three primary partitions + one extended with as many logical partitions as you want without fiddling with MBR compatibility mode mumbo-jumbo.

---

### Post by billbear on 2008-05-06
> **cyberdork33 said:**
> 

However, the 4 partition "limit" is a limitation of the emulated MBR partition table and is always the first 4 partitions in your GPT. 

You can also manually edit the MBR partition table to use any subset of the GPT, but the first partition of MBR table has to be the 200M protected EFI partition, otherwise the GPT table will be erased upon next boot.

---

### Post by billbear on 2008-05-06
> **benanzo said:**
> Just to throw another angle into the mix here, I was booting Windows XP, Mac OS X and Ubuntu off a pure MBR disk (no GPT at all) for quite awhile and it worked great.  It's quite involved and over-complicated but definitely doable.  I just used GRUB as the global bootloader rather than refit.  Basically it boils down to installing OS X like normal, then booting a live disc and making the installation into a tarball on an external disk, changing the partition scheme, then untarring OS X back onto it's partition.  This allows for the three primary partitions + one extended with as many logical partitions as you want without fiddling with MBR compatibility mode mumbo-jumbo.

If you want to change the disk to pure MBR, simply delete the hidden 200M partition from MBR table and upon next boot the GPT table will be erased. But if you reinstall OS X, you will have to erase the whole disk. And you will not be able to upgrade firmware without GPT.

---

### Post by cyberdork33 on 2008-05-06
> **billbear said:**
> You can also manually edit the MBR partition table to use any subset of the GPT, but the first partition of MBR table has to be the 200M protected EFI partition, otherwise the GPT table will be erased upon next boot.

> **billbear said:**
> If you want to change the disk to pure MBR, simply delete the hidden 200M partition from MBR table and upon next boot the GPT table will be erased. But if you reinstall OS X, you will have to erase the whole disk. And you will not be able to upgrade firmware without GPT.wow good to know.

do you have a how-to or more technical information on creating a MBR table the way you want?

---

### Post by billbear on 2008-05-06
I just type sudo fdisk -e /dev/rdisk0

then edit 2
Do you wish to edit in CHS mode? [no] 
Partition offset: see refit partition inspector report
Partition size: calculated from refit partition inspector report

then edit 3, edit 4

---

### Post by billbear on 2008-05-06
I tried this with an external disk, with my internal disk removed from my macbook, thus the partition inspector will see the external as internal and give me the report.
I don't know if there is a command that can list the GPT table in sectors.

---

### Post by PartisanEntity on 2008-11-06
Could someone explain this in simpler terms. I want to create a 5th partition, using FAT32, to use as a shared drive between Leopard and Ubuntu 8.10 on my macbook.

Where do I position this partition, and the 'end', i.e. after my /swap partition? And if I do this can both operating systems access this partition?

Thank you.

---

### Post by cyberdork33 on 2008-11-06
> **PartisanEntity said:**
> Could someone explain this in simpler terms. I want to create a 5th partition, using FAT32, to use as a shared drive between Leopard and Ubuntu 8.10 on my macbook.

Where do I position this partition, and the 'end', i.e. after my /swap partition? And if I do this can both operating systems access this partition?

Thank you.
You don't have an issue with the 4 partition "limit" as long as you are not trying to boot from the 5th partition.
i.e. you can create a 5th partition formatted as FAT32 and it should work for both OSs as is.

---

### Post by PartisanEntity on 2008-11-06
> **cyberdork33 said:**
> You don't have an issue with the 4 partition "limit" as long as you are not trying to boot from the 5th partition.

Got it, thanks.

---

### Post by PartisanEntity on 2008-11-07
Ufortunately I have run in to a problem.

I created a FAT32 parition which I placed after my swap partition.

Now rEFIt only shows the OSX and FAT32 partitions as boot options? I ran the rEFIt partition analyzer and still the same problem. Ubuntu is missing from the list.


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    139669109  Mac OS X HFS+
 3      139669110    199173869  Basic Data
 4      199173870    209857094  Linux Swap
 5      209857095    234436544  MS Reserved

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    139669109  af  Mac OS X HFS+
 3 *    139669110    199173869  83  Linux
 4      199173870    209857094  82  Linux swap / Solaris

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 139669110:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux, active

Partition at LBA 199173870:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris

Partition at LBA 209857095:
 Boot Code: Unknown, but bootable
 File System: FAT32
 Listed in GPT as partition 5, type MS Reserved

---

### Post by cyberdork33 on 2008-11-07
The "Basic Data" partition is your Ubuntu partition.

You probably need to install GRUB again to the root partition (/dev/sda3). You can boot a LiveCD and do this. This is shown here:
[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

---

### Post by PartisanEntity on 2008-11-07
Thanks very much, worked and am now back in Ubuntu

---

### Post by PartisanEntity on 2008-11-07
Now that I finally have my 5th partition, I can access it from Ubuntu but can't mount it in Leopard.

Any ideas?

Current GPT partition table:
# Start LBA End LBA Type
1 40 409639 EFI System (FAT)
2 409640 139669109 Mac OS X HFS+
3 139669110 199173869 Basic Data
4 199173870 209857094 Linux Swap
5 209857095 234436544 MS Reserved

Current MBR partition table:
# A Start LBA End LBA Type
1 1 409639 ee EFI Protective
2 409640 139669109 af Mac OS X HFS+
3 * 139669110 199173869 83 Linux
4 199173870 209857094 82 Linux swap / Solaris

MBR contents:
Boot Code: Unknown, but bootable

Partition at LBA 40:
Boot Code: None (Non-system disk message)
File System: FAT32
Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
Boot Code: None
File System: HFS Extended (HFS+)
Listed in GPT as partition 2, type Mac OS X HFS+
Listed in MBR as partition 2, type af Mac OS X HFS+

Partition at LBA 139669110:
Boot Code: GRUB
File System: ext3
Listed in GPT as partition 3, type Basic Data
Listed in MBR as partition 3, type 83 Linux, active

Partition at LBA 199173870:
Boot Code: None
File System: Unknown
Listed in GPT as partition 4, type Linux Swap
Listed in MBR as partition 4, type 82 Linux swap / Solaris

Partition at LBA 209857095:
Boot Code: None (Non-system disk message)
File System: FAT32
Listed in GPT as partition 5, type MS Reserved

---

### Post by cyberdork33 on 2008-11-07
It seems that your fifth partition got the MS Reserved flag set in the GPT. This causes the partition to become inaccessible in OS X. It seems to be a bug in gparted. Here is some info about it.

[http://discussions.apple.com/thread.jspa?threadID=1359951&tstart=4290](http://discussions.apple.com/thread.jspa?threadID=1359951&tstart=4290)
[http://www.macosxhints.com/article.php?story=20080130022147512](http://www.macosxhints.com/article.php?story=20080130022147512)
[http://forum.insanelymac.com/lofiversion/index.php/t31562.html](http://forum.insanelymac.com/lofiversion/index.php/t31562.html)

---

### Post by Mattventura on 2008-11-08
I have found that most of the problems related to the GPT partition table can be solved by going MBR-only. OS X does not need a GPT. From what I remember when I did it, you first blank out the EFI protective partition, then delete it, and you can use the freed 4th partition to make an extended partition (which you can now do if you couldn't previously due to the GPT) and put logical partitions in the extended partition.

I recommend backing up your MBR before you do this just in case something happens.

---

### Post by PartisanEntity on 2008-11-08
> **cyberdork33 said:**
> It seems that your fifth partition got the MS Reserved flag set in the GPT. This causes the partition to become inaccessible in OS X. It seems to be a bug in gparted. Here is some info about it.

[http://discussions.apple.com/thread.jspa?threadID=1359951&tstart=4290](http://discussions.apple.com/thread.jspa?threadID=1359951&tstart=4290)
[http://www.macosxhints.com/article.php?story=20080130022147512](http://www.macosxhints.com/article.php?story=20080130022147512)
[http://forum.insanelymac.com/lofiversion/index.php/t31562.html](http://forum.insanelymac.com/lofiversion/index.php/t31562.html)

Thanks very much for pointing that out. This turned out to be the issue. I was able to get rid of the flag and now the FAT32 partition mounts nicely in both Leopard and Ubuntu :)

---

### Post by cyberdork33 on 2008-11-08
> **Mattventura said:**
> I have found that most of the problems related to the GPT partition table can be solved by going MBR-only. OS X does not need a GPT. From what I remember when I did it, you first blank out the EFI protective partition, then delete it, and you can use the freed 4th partition to make an extended partition (which you can now do if you couldn't previously due to the GPT) and put logical partitions in the extended partition.

I recommend backing up your MBR before you do this just in case something happens.

The only problem with that is that OS X will not install on an MBR disk, but there are a few people that run on an MBR disk... especially those that single boot.

> **PartisanEntity said:**
> Thanks very much for pointing that out. This turned out to be the issue. I was able to get rid of the flag and now the FAT32 partition mounts nicely in both Leopard and Ubuntu :)
Can you detail what you did? Some users have trouble with this quite often.

---

### Post by PartisanEntity on 2008-11-08
> **cyberdork33 said:**
> 
Can you detail what you did? Some users have trouble with this quite often.

My method was rather primitive:

Using the Ubuntu LiveCD launch the partition editor and delete the FAT32 partition. 

Replace it with a resierFS partition.

Why do we do this: 

a) the partition editor sets no flags on reiserFS partitions it creates
b) the Disk Utility (which we will need in the next step) in OSX can't edit ext2/3 partitions, neither can it erase a FAT16, FAT32 or NTFS partition that is flagged with *MS Reserved*.

Next launch OSX and open Disk Utility.

Now click on the resierFS partition and select 'erase'. 

Erase the reiserFS partition and replace it with a FAT32 partition (choose the FAT from the drop down menu). 

Disk Utility will create a FAT32 partition without any flags and this new partition will mount nicely in both OSX and Ubuntu.

---

### Post by cyberdork33 on 2008-11-08
> **PartisanEntity said:**
> My method was rather primitive:

Using the Ubuntu LiveCD launch the partition editor and delete the FAT32 partition. 

Replace it with a resierFS partition.

Why do we do this: 

a) the partition editor sets no flags on reiserFS partitions it creates
b) the Disk Utility (which we will need in the next step) in OSX can't edit ext2/3 partitions, neither can it erase a FAT16, FAT32 or NTFS partition that is flagged with *MS Reserved*.

Next launch OSX and open Disk Utility.

Now click on the resierFS partition and select 'erase'. 

Erase the reiserFS partition and replace it with a FAT32 partition (choose the FAT from the drop down menu). 

Disk Utility will create a FAT32 partition without any flags and this new partition will mount nicely in both OSX and Ubuntu.
Great, thanks. That is a good work around.

---

