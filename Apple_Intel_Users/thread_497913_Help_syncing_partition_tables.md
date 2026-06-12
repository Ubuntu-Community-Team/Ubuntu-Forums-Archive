---
title: "Help syncing partition tables"
date: 2007-07-10
forum: Apple Intel Users
---

### Post by asoare on 2007-07-10
Hello,

I have a question regarding the triple boot Os X / Vista / Ubuntu.

I have successfully installed vista, BUT: Before installing vista I created a fat32 for it. During the vista setup, i deleted the partition for vista and created a new, bigger one, ntfs. Now my partition tables are out of sync. From what I see, syncing with gptsync will overwrite my mbr with gpt, this destroying my vista partition. True or not? how do I sync them without loosing windows? :-s

Thank you for your time.

---

### Post by ronocdh on 2007-07-10
You aren't using rEFIt? REFIt supports table syncing right from the main screen; just go to the partioning option and it'll ask for permission to sync if your tables need it. Once that's performed, exit out and hopefully you can boot normally at that point.

---

### Post by asoare on 2007-07-11
Yes, I am using refit and it detected that they are out of sync, but I think syncing them will overwrite my mbr and thus destroy my windows partition.

As I was saying, GPT contains old, inexistent partitions. MBR has the right configuration. And refit asks me if i want to overwrite MBR with GPT. 

How do I sync them without damaging windows ?

---

### Post by asoare on 2007-07-11
I think I blew my triple boot setup :) I need some help.

Here's what I did, exactly: I created with diskutil resizevolume in OS X 3 more partitions: one for linux, one for data storage (fat32) and one for windows (fat32) in this order.

Then, I booted from vista install dvd and used the grafical partitioning tool from windows setup. I deleted the 2 fat32 partitions, because I wanted ntfs and I couldn't create ntfs with diskutil. I created one ntfs partition for windows and left some unallocaed space.

FInally, I installed vista successfully, but my tables were out of sync. And so I posted this thread.

And now I have used the sync tool from refit, which overwrote MBR and so my windows partition is now GONE :( now the mbr contains the initial 3 partitions which i had first created with diskutil.

So, to conclude, how do I install windows, this time successfully ?
What I want is the following:

- mac partition
- linux partition(s)
- ntfs windows partition
- a partition for storage, I don't want fat32. I prefer ntfs, but I don't know, is there any other type which the 3 OSes can easily detect and work with better than ntfs ?

And how do I keed the partition tables in sync without destroying some partitions, like it happened now.

---

### Post by cyberdork33 on 2007-07-11
you need to use a partitioner that writes GPT to create the partitions the size that you want to begin with. The problem is that the Windows installer will not alter the GPT, only the MBR, so refit will always say they are out of sync if you just use windows to partition.

You should be able to use something like parted to edit the GPT now to the same size as the partitions really are, and not lose your install.

---

### Post by asoare on 2007-07-11
Can you please be a little more specific? I don't know too much about linux and os x, i'm a windows guy.

I only have access to Os X and I see parted is for linux. So what do I use and how ? .. to partition my drive.

---

### Post by cyberdork33 on 2007-07-11
You always have access to linux. That's what LiveCD's are for. 

Here is a thread explaining how parted works. It is based on resizing a OSX partition, but it details how to use the command which is what you need.
[http://ubuntuforums.org/showthread.php?t=89960](http://ubuntuforums.org/showthread.php?t=89960)

You can try using diskutil but I am not sure how the NTFS thing will play into things. 

Also, to support my reply, you came to a linux forum asking for how to do something, I assume that you are looking for a linux answer...

You might also look into gparted. They have a livecd. I think that they support gpt now.

---

### Post by asoare on 2007-07-11
I can't seem to make the live cd work. I have The ubuntu 7 live cd, it boots from it, the graphical menu appears, i choose start or install ubuntu, it liads and then a black screen appears and it says:

Busybox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands

/bin/sh: can't open tty; job control turned off
(initramfs): _

---

### Post by cyberdork33 on 2007-07-11
likely a bad burn / download. try to verify the disk.

---

### Post by asoare on 2007-07-11
No, I have installed ubuntu from that CD on my desktop PC and it works smoothly. 
I have also tried to boot from kubuntu 7 live cd - same thing.
With Ubuntu 6 live cd (build date: 7 july 2006), something else happens: Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. And then i press yes for details and says: No devices detected. Fatal server error: no screens found.

By the way - the laptop laptop i'm trying to do the triple boot on is a macbook pro with 2 GB RAM. (the new santa rosa model)
I should also note that I already have 4 primary partitions on the drive, if it makes any diffference.

I booted from the gparted live cd, I see that works but I have no ideea how to work with it :) all i have is a command line. Anyway, even if i manage to get my partitions right with it (i don't know how yet), there will still be a problem with installing ubuntu :-s

---

### Post by cyberdork33 on 2007-07-11
Yea. You are really only going to be able to have 4 partitions is you want everything to cooperate. The SantaRosa machines are a bit special, unfortunately. They do not have great support currently (new hardware). I would check out the Santa Rosa threads for answers to those issues.

Most everyone triple-booting has 4 partitions:
EFI, OSX, Ubuntu, Windows
That is really the only way to do it.

I am kinda doubting that the gparted cd is going to work on the santa rosa machine. It should start up Xorg and have a nice graphical partitioner.

---

### Post by asoare on 2007-07-12
What I actually need is a partitioning tool that supports mac partitions and ntfs. Is there no such thing ? for os x or maybe from a live cd ... ?

Or .. if it is possible to sync MBR and EFI by copying mbr to efi ?

---

### Post by cyberdork33 on 2007-07-12
you are going to have to use the tools in OSX (diskutil) or buy something like iPartition. As far as I know, the partition tables sync one way gpt>mbr not the other way.

gparted does seem to work ok (used it to move a hfs+ partition last night. I did have to do repairs on the partition afterwards though.), although you need to use refit to sync everything afterwards. The problem is that you have a Santa Rosa machine which has troubles with linux right now. Check the Santa Rosa threads to see what you might need to do to get xorg to start, then you can use the live cd with special options (maybe).

---

### Post by asoare on 2007-07-12
iPartition doesn't work with windows / linux partitions, just os x.
diskutil is what i used so far and look where i'm at :P

you mean it's not apple's fault for the linux problem ? all santa rosa laptops behave this way with linux ?

---

### Post by cyberdork33 on 2007-07-12
> **asoare said:**
> iyou mean it's not apple's fault for the linux problem ? all santa rosa laptops behave this way with linux ?

well that is kind of a loaded question...

No, it is is not apple's fault, and yes it is at the same time. Apple doesn't 'support' running linux on their machines, so they do not make any attempt to include linux-compatible hardware. So they update hardware without any regard to whether it will break linux (and probably don't care really). So yes, it is Apple's fault that they break linux compatibility, but no, because they have no reason not to break it... They have their own OS that works just splendidly.

It is not linux's fault because, well, it is new hardware, and it takes time for developers to make everything work. It is not any more helpful that Apple uses closed hardware (like broadcom) and their own proprietary, different from everything else, configurations. This is pretty much standard when new hardware comes out. For more information on the Santa Rosa issues, check out this thread:
[http://ubuntuforums.org/showthread.php?t=474144](http://ubuntuforums.org/showthread.php?t=474144)

If you cannot create anything but OSX partitions with iPartition, then IDK. (I don't use any partitioners under OSX). You can use the 'diskutil resizeVolume' to resize your osx partition to the whole disk and start over, which might be the easiest thing to do in this case. If you use diskutil to create all your partitions at once, (and don't erase them and resize them afterwards like you did), then you shouldn't have an issue with the gpt getting out of whack.

---

### Post by asoare on 2007-07-13
ok, I managed to get into Linux, I used gparted successfully, made my ntfs storage partition, but unfortunately it is still a primary partition, so windows will not recognise it. how do i make it logical partition?

---

### Post by thully on 2007-07-13
One thing I'd like to point out is that you are *NOT* limited to 4 partitions (3 not counting the EFI partition).  Except in Windows, which can't see any partitions beyond 4, you are only limited to 4 (3 not counting EFI) *boot* partitions.  Currently, I have my Linux swap as partition 5 and it works great.  As long as your boot partitions are among the first 4, and as long as you don't want to use anything beyond part. 4 in Windows, you're fine.

One thing - you don't want an NTFS storage partition, unless it is for Windows only.  If you want a shared storage partition, FAT32 is the only way to go if you're using Windows (non-journaled HFS+ works well if you're just doing OSX/Linux).

---

### Post by cyberdork33 on 2007-07-13
having more than 4 primary partitions has been causing some issues with refit for some people. Having swap as number 5 should be fine though since you can't boot from swap.

As for the logical partition question. I don't think it can be done on a gpt disk (remember your mac only emulates a BIOS and MBR)

---

### Post by asoare on 2007-07-13
> **thully said:**
> One thing I'd like to point out is that you are *NOT* limited to 4 partitions (3 not counting the EFI partition).  Except in Windows, which can't see any partitions beyond 4, you are only limited to 4 (3 not counting EFI) *boot* partitions.  Currently, I have my Linux swap as partition 5 and it works great.  As long as your boot partitions are among the first 4, and as long as you don't want to use anything beyond part. 4 in Windows, you're fine.

First, I hope you mean windows can't see beyond 4 *primary* partitions, because it can have much more logical partitions and everything will be ok.

Is it possible to make the linux partition number 5 and swap number 6 ?
So the order would be: 1-EFI, 2-MAC, 3-Windows, 4-Storage, 5-Linux, 6-Swap
This way windows will see the storage partition. 
But will linux boot from 5th partition ?


> One thing - you don't want an NTFS storage partition, unless it is for Windows only.  If you want a shared storage partition, FAT32 is the only way to go if you're using Windows (non-journaled HFS+ works well if you're just doing OSX/Linux).

Yes, I want ntfs because fat32 can't hold files larger than 4GB. And I want to be able to access it from windows.

> As for the logical partition question. I don't think it can be done on a gpt disk (remember your mac only emulates a BIOS and MBR)

From windows, it can be done. But that will not create it in the EFI partition table unfortunately, so I don't want to make it from windows.

---

### Post by cyberdork33 on 2007-07-13
> **asoare said:**
> From windows, it can be done. But that will not create it in the EFI partition table unfortunately, so I don't want to make it from windows.

That is kinda my point. there is no way to to make a logical partition in a GPT (GUID partition table, which is what is used on your mac.) because there is no need for them. Logical partitions are really a 'hack' to get around the 4 partition limit. I think being able to designate certain partitions as logical in your MBR is going to take some new tools.

I am pretty sure that linux will not boot from partition 5 since the bootloader can only see the first 4. (This is why your bootable partition has to be a primary partition.) plus windows likes to be last (partition4) or at least that used to be a problem for multibooters.

Now, On the other hand... (this is gonna sound crazy, but I actually have something similar working). You can put your OSX partition AFTER 4. OSX has not problem booting from any partition because it boots directly from EFI. Now, I would try this at your own risk. My setup is as follows:

1. EFI
2. OSX install 1
3. swap
4. Ubuntu
5. OSX install 2

I have had no issue booting from either OSX partition. Don't ask why I have 2. rEFIt sees  all three OS's and gives me the option to boot any of them.

So, from that information, it may be possible to move OSX to the end of your disk, and then put some partitions between EFI and OSX. I would make a full backup before trying this. but I actually moved my second OSX install with gparted, then booted from the install DVD and did repairs on the filesystem and it has worked great.

---

### Post by asoare on 2007-07-13
I'm thinking about:
1.EFI
2.Linux
3.Storage
4.Vista
5.Mac
6.Swap

I guess I'll try, I have no other option and nothing to loose :)

Oh and I currently have Vista on 3rd and it works, maybe XP wanted the 4th partition, but vista is ok with 3 :)

> I think being able to designate certain partitions as logical in your MBR is going to take some new tools.
You mean from outside windows ? Could it be possible ?

Btw I've tried to make a logical partition from Vista from that unallocated space (which was supposed to be the 5th), just to see if MBR will still be in sync with EFI and something weird shows up: it tells me that in order to do this, it will convert my basic disk to dynamic disk. weird. pressed ok once and turned all my partitions to raw. i'm lucky i don't have any real data, I just bought it :)

---

### Post by cyberdork33 on 2007-07-13
> **asoare said:**
> I'm thinking about:
1.EFI
2.Linux
3.Storage
4.Vista
5.Mac
6.Swap

I guess I'll try, I have no other option and nothing to loose :)

Oh and I currently have Vista on 3rd and it works, maybe XP wanted the 4th partition, but vista is ok with 3 :)

Yea it seems that people are having it easier now with Vista.

Hope that scheme works out for you. If the swap doesn't pan out, it probably won't hurt you too much.

> You mean from outside windows ? Could it be possible ?
Yea I mean like in gptsync (tool that syncs GPT and MBR) It would have to be able to map a logical partition in the MBR to a real partition in the GPT. Something that can't be done that I know of. not yet anyway. I mean you can make logical partitions with lots of tools... fdisk, cfdisk, parted, etc. I just don't think it will work in the Mac's emulated Bios structure.

---

### Post by asoare on 2007-07-15
Wow, it really works :) that was a great ideea !
Now, how do I remove my storage partition from refit menu ? :) It appears with a windows icon. Can I remove it ?

---

### Post by benanzo on 2007-07-15
OS X doesn't actually use the EFI partition for anything.  It reads the EFI info directly off the OS X boot partition.  The first partition (EFI) is only there for compatibility with Intel's EFI spec, but isn't used.

My method for triple-booting:

1) Install OS X normally
2) Clone or make a tarball of OS X and move it to an external disk.
3) Boot Ubuntu LiveCD - repartition the disk as MS-DOS/MBR (NO GPT):
---1 - OS X *HFS+*
---2 - Windows *NTFS*
---3 - Ubuntu *EXT3*
---4 - Extended
-------5 - Home (Ubuntu) *EXT3*
-------6 - Swap *swap*
-------7 - Storage - *no filesystem yet (will be FAT32 for compatibility)*

4) Install Windows first to partition 2
5) Install Ubuntu to partition 3
6) Boot to Ubuntu and copy your OS X system to partition 1
7) Now reinstall GRUB to the disk's MBR - Do update-grub to update your menu.lst


Now you can boot all three OSs from the GRUB menu without having anything to do with EFI/GPT.  OS X will boot and run just fine from an MBR disk.  However, it will refuse install to one, that's why we had to clone it at the beginning.  Don't format the FAT32 storage partition until after Windows has been installed.  The Windows installer is freakin' dumb and will crap out if it doesn't see anything it can work with.  That's why we formatted partition 2 as NTFS from the Ubuntu LiveCD (so Windows would find it early and not complain.)

---

### Post by cyberdork33 on 2007-07-15
> **benanzo said:**
> OS X doesn't actually use the EFI partition for anything.  It reads the EFI info directly off the OS X boot partition.  The first partition (EFI) is only there for compatibility with Intel's EFI spec, but isn't used.

This is true, but I wouldn't say that it will not be used in the future.

---

### Post by asoare on 2007-07-16
Well as I said it works perfectly, so I'll leave it as it is ... for now.

@benanzo: your ideea sounds ok, but I don't understand something:
- how do I repartition the disk as MS-DOS/MBR ? 
- do I need to delete de first partition (EFI - boot) ?

As for my current setup, I have a couple of minor inconveniences:

1. The storage partition, being a primary ntfs partition, always shows up in refit menu and if i click on it nothing boots. Can I remove it from the refit menu? How ?

2. Ubuntu has mounted by default the vista and storage partitions. Can I also mount Os X partition?

3. When I boot from Vista install dvd and click repair, it doesn't detect any Vista installed. Why not ?

---

### Post by cyberdork33 on 2007-07-16
> **asoare said:**
> 1. The storage partition, being a primary ntfs partition, always shows up in refit menu and if i click on it nothing boots. Can I remove it from the refit menu? How ?
Probably not. rEFIt sees the drive as a bootable partition, so it adds it to the selection.

> 2. Ubuntu has mounted by default the vista and storage partitions. Can I also mount Os X partition?yes. There are several threads on sharing home partitions and mounting HFS+ partitions in linux. (and mounting ext3 partitions in OSX)

> 3. When I boot from Vista install dvd and click repair, it doesn't detect any Vista installed. Why not ?Can't really help you there. Maybe because it is not the first partition or something.

---

### Post by benanzo on 2007-07-16
It is only necessary to remove the EFI partition if you want to set up your system the way I did, or similar.  The EFI partition is only 200Mb with a standard FAT32 filesystem.  Like I said, Apple doesn't currently use this partition for anything.  It is only there for compatibility with Intel's EFI specification.  But as was mentioned by *cyberdork*, there is no guarantee that Apple wont push an update that requires that partition.  However, I find it highly unlikely that  they would roll an update that shifted Tiger's boot code to an entirely different partition so late in its life.  That spells disaster.  If anything, I would suspect that any change to the EFI boot process will arrive in Leopard, not as an update to Tiger.  That is why it feels reasonably safe to get rid of that (currenty) worthless waste-of-space.

You can change the disk to MS-DOS (MBR) by opening GParted in Ubuntu and selecting **Device -> Set disklabel** then setting it as **ms-dos**.  Beware that this will effectively wipe the entire disk.  You need to do this *before* you install anything.

As I said, first step is to install OS X normally.  It will create two partitions by default.  The worthless EFI partition and the system partition.  When the install is done, boot to the Ubuntu LiveCD and make a tarball of the OS X system partition.  Then open GParted and set the disk as ms-dos.  Then create all your partitions and follow the rest of the steps above.

Good Luck!

---

### Post by [woodstock] on 2007-07-18
@benanzo:
Did you perform any firmware updates with your configuration yet? [This page]("http://refit.sourceforge.net/myths/") hints that there coud occur some problems if the EFI partition and/or the GPT is missing.


Does anyone have reliable information or sources about what is possible and what isn't in respect to partitioning MacBooks? [This page]("http://refit.sourceforge.net/tripleboot/") states that the number of partitions for a hybrid configuration is limited to 4 paritions without explaining from where this limitation originates.
[This guy]("https://cbg.dyndns.org/wiki/ReadingCorner/LinuxOnMacbookPro") also says that there is a 4 partition limit. However, he offers a workaround using LVM on one of these partitions.
In this thread "asoare" at least succeeded to create 6 paritions on his disk, seemingly without running into problems.
So, does anyone know where the actual limitations are?

Having more than 4 partitions is quite useful if one intends to separate /home from the rest of the system. /swap and a shared partition which can be used from other OS as well makes at least 4 partitions for a (my) linux system.

---

### Post by cyberdork33 on 2007-07-18
As long as they are not boot partitions they can be after the first 4 partitions. (unless it can boot directly from EFI and is not using the emulated BIOS.)

Again, the 4 partition limit is a legacy BIOS limitation.

---

### Post by benanzo on 2007-07-18
> @benanzo:
Did you perform any firmware updates with your configuration yet? This page hints that there coud occur some problems if the EFI partition and/or the GPT is missing.

Yes I have done every firmware update that Apple pushed starting with 10.4.6 up to current without a GPT - no problems.  The 10.4.6 update was a big one because that was when Apple updated the actual EFI firmware to allow for limited BIOS emulation.  Unfortunately Apple isn't 100% compliant with Intel's EFI specification, which is supposed to implement the BIOS emu and hybrid GPT/MBR support from the start.  I don't really trust EFI (because there are a few closed bits) and I certainly don't trust Apple's implementation of EFI (because they don't adhere to all the specs.)  That is why we're having a hard time booting Linux directly from Apple's EFI (without BIOS emu).  Apparently Apple has some secret way of getting graphics info out of the framebuffer so the best I can get is 800x600 with the vesa driver, which is unusable.  But just using the BIOS emu and setting up the disk as I did with just an MBR works great.

I can't wait to boot in EFI mode though, GRUB2 is trying to solve that problem.  Look for it in Gutsy+1.  Even more so, I cant wait until LinuxBIOS supports the MacBook (which wont be anytime soon).  Boot time with LinuxBIOS would be about 10 secs...you can set the BIOS to boot the kernel directly (without GRUB).  Awesome.

---

### Post by [woodstock] on 2007-07-18
If I understand the rEFIt pages correctly, then the BIOS emulation is mandatory due to graphic accelleration (both, 2D and 3D). Hence, there is no way *not* to use BIOS compatibility, especially if one needs Windows, too.

I still wonder where this 4 partition limitation came from? Is it a limitation of *primary* partitions or does it affect the overall number of partitions? The former would explain its connection to BIOS compatibility mode. If that's so, then one could format a HDD like this, because there is no limitation for logical discs?

200 MB EFI        ("primary")
5 GB OSX        ("primary")
5 GB /root        ("primary")
100 GB           ("extended")
    2 GB          SWAP (as "logical)
    4 GB          /home (as "logical")
   94 GB         /media/share (as "logical")

---

### Post by [woodstock] on 2007-07-18
> **benanzo said:**
> Yes I have done every firmware update that Apple pushed starting with 10.4.6 up to current without a GPT - no problems.

That's good news.
I do not actually own a MacBook yet. This is why I want to know if everything important to me would run as I expect it to or at least where I can expect to run into trouble.

Is this MBR thing fully reversible ,i.e. could I put the MacBook back in the condition I bought it if something would go terrible wrong by installing MacOS anew from CD?

---

### Post by benanzo on 2007-07-18
Yes, you can reverse the MBR to GPT or MBR/GPT hybrid anytime you want.  However, you will have to reinstall your OS(s) if you do that because changing the disklabel effectively formats the disk.  Be sure to take a backup before doing it.

The MBR (which is only used in BIOS-based systems) can have up to 4 Primary (bootable) partitions plus any number of Extended (non-bootable) partitions.  When I say that they're "bootable" or "non-bootable" I am specifically referring to being recognized as a boot disk from the BIOS.  GRUB can boot systems installed on an Extended partition just fine.  Since this is the case, you can effectively install twenty different OSs on one machine and boot them all with GRUB.  Keep in mind that if you want to add extended partitions to an MBR disk the **Extended** entry in the MBR counts as one primary partition.  So you are left with only three usable Primaries.

By contrast, a GPT or GUID Partition Table, doesn't support Extended partitions at all.  However, it is not limited to just four primary partitions; it supports up to 128.  But this is not useful if you need to use BIOS emulation to boot your systems since you will still be constrained by the MBR even in a GPT/MBR hybrid.

The issue, as it boils down, is that you can't use Extended partitions if you have an MBR/GPT hybrid (as with bootcamp or refit) because they have to be in sync.  You can't use just GPT because then you'd have to boot in pure EFI (which isn't a good idea right now for graphics reasons, not to mention that it is simply not and will never be possible with 32 bit Windows.)  The best I've come up with is to use a single MBR (no GPT) so that I can use Extended partitions, boot in emulated BIOS mode and use GRUB to get all my systems up and running.  It's kind of a kludge, but it works very well for now.

---

### Post by [woodstock] on 2007-07-18
@benanzo:
Thank you very much for the enlightenment. So there is no problem using OSX on MBR disks, except for installing OSX onto one of them.
Is this backup and restore solution you pointed out earlier straight forward, i.e. is a simple dd and "re-dd" sufficient or are there some traps?

Thanks again for your explanation.

---

### Post by benanzo on 2007-07-18
I actually just use TAR to backup and restore.  It is a little slower but ultimately I think it is better for portability since the entire OS (whether Linux, Mac or Windows) can be contained in a single .tar.gz archive.

[Here]("http://ubuntuforums.org/showthread.php?t=35087") is a really good tutorial for backing up your system with TAR.

---

### Post by asoare on 2007-07-21
> **benanzo said:**
> The best I've come up with is to use a single MBR (no GPT) so that I can use Extended partitions, boot in emulated BIOS mode and use GRUB to get all my systems up and running.  It's kind of a kludge, but it works very well for now.

Why do you say *emulated* BIOS ? isn't it native if you set the disklabel to msdos ?

Oh, and in your setup (MBR only), if you want to install Leopard when it launches, will you have to format your entire disk so you can set it again to EFI/MBR hybrid so that you can install Leopard?

> Yes I have done every firmware update that Apple pushed starting with 10.4.6 up to current without a GPT - no problems. 

Are there any firmware updates for the Santa Rosa models launched recently ? I didn't find any ... if there are please give me a link, as I could not find them.

---

### Post by cyberdork33 on 2007-07-21
The new Intel macs use EFI not a bios. Therefore to boot legacy OS's it must emulate a BIOS.

---

