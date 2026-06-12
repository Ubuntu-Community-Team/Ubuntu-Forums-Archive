---
title: "[SOLVED] Trouble installing Kubuntu 7.10 on a Mac Pro"
date: 2007-11-18
forum: Apple Intel Users
---

### Post by street spirit on 2007-11-18
I'm having trouble installing Kubuntu Gutsy on a Mac Pro.
Sorry for being a little verbose, but I guess this will help other people who run into the same problem find the thread more easily.

My setup:
- NVIDIA GeForce 7300
- HD Bay 1: 1TB disk containing OSX 10.5 Leopard and Windows XP
- HD Bay 2: 240GB disk (empty)
- Eizo FlexScan S2431W monitor connected via DVI
- 5GB of RAM

What I did before:
- installed OSX Leopard
- installed rEFIt
- started Boot Camp Assistant, and let it resize my Leopard partition
- installed WinXP on a 150GB partition on the first HD
- installed the Boot Camp drivers in WinXP

Up to here, everything was working perfectly. I was originally planning to put Linux on the first HD as well, but then I decided to put it on the second (because OSX and WinXP were working together so nicely).

I then inserted the Kubuntu live CD (v7.10, amd64) and rebooted. rEFIt showed an icon for the Linux CD, and I entered the Kubuntu live CD menu. When I selected "Start or install Kubuntu", the system began to start up alright, and I got to the animated loading screen. Then (around the point where X would be loaded) artifacts began to appear on the screen and the animation stopped. Still, KDE seemed to load OK, because I could hear the welcome sound. At this point, the display was a mess, and I couldn't see a thing. Sometimes my monitor even went into standby. Anyway, no usable display.

When I chose the second option from the disk menu ("Start Kubuntu in safe graphics mode"), the artifacts still appeared, but after a while they were cleared, and I got to the KDE desktop. I started the graphical installer.

This is my partition layout:
```

sdb1: EFI      -                fat32      200MB
sdb2: Linux    /                ext3       25GB
sdb3: Linux    /home            ext3       73GB
sdb4: swap     -                swap       5.5GB        (for hibernate; I'm an optimist :-)
sdb5: shared   /media/shared    fat32      140GB
```
Other than that, I only removed the "mount point" entries for the two EFI system partitions (sda1 and sdb1).

The next (=last) page of the installer showed that all changes would be to SCSI4 (0,0,0) which I assume is the disk in bay 2. As stated [[COLOR="Blue"]_in this forum message_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=594298"), I clicked the "Advanced..." button on that page to tell the installer where to put the grub bootloader. The following form popped up:

| Boot loader
|
| [x] Install boot loader
|
| Help for GRUB device selection goes here.
| [(hd0)________________]

The "help for.. goes here" part suggests that somebody forgot to translate this text or something, which is very unfortunate, because I fear that this is exactly the point where I make my mistake. I entered "/dev/sdb2", because that's where my kernel is going to be (I hope). Syntactically this is quite different from "(hd0)", but the installer didn't give me any errors, so I continued and clicked "Install".

The install finished normally without errors. I did get errors when I tried to reboot or shutdown: screens full of error messages like "SQUASHFS error: unable to read [...]" and the like, until I just shut the thing down with the power button (by the way, a reset button would have been nice, Apple). After that the Mac booted normally into rEFIt, which showed two additional icons:

- [penguin] Boot Linux from
- [dummy img] Boot Legacy OS from HD

I tried them both, and in both cases there was some delay, and then Windows started (which is weird, because the Windows partition is not the active startup disk). In any case, no Linux =(

After that I tried another Kubuntu install disk: the full DVD this time, and the i386 version. I had downloaded it earlier before I realized that I should be using the 64bit version. The result was similar, except that I didn't even get to see the SQUASHFS errors, because the system seems to have crashed silently before that.



And now I'm stuck.
Any ideas?

---

### Post by cyberdork33 on 2007-11-19
As far as I have seen, you are doing things correctly. the syntax you used to install grub should be OK in the Ubuntu installer (the other syntax is Grub's syntax, which is a bit different.)

There is a thread where someone was trying to install on a completely seperate hard drive on a Mac Pro previously, and this problem seems to ring a bell:
[http://ubuntuforums.org/showthread.php?t=553587](http://ubuntuforums.org/showthread.php?t=553587)

It seems that the Mac Pro Hard drives are detected very strangely for some reason. Once grub loads, it sees the disk that it is installed to as the primary disk (hd0) maybe? I would try to make a similar edit as the person in the above thread and see if that works for you. You can so this by booting the live cd and mounting your partition and editting the file.

You could also, start terminal from the live cd, type 'grub' then enter the following command and see what it returns:
```
find /boot/grub/stage1
```
This should tell you the device that grub THINKS it is installed to.

---

### Post by street spirit on 2007-11-19
Thank you.

> **cyberdork33 said:**
> It seems that the Mac Pro Hard drives are detected very strangely for some reason. Once grub loads, it sees the disk that it is installed to as the primary disk (hd0) maybe?

I don't think I even get to the part where grub gets loaded; at least I don't see anything on the screen.

> **cyberdork33 said:**
> I would try to make a similar edit as the person in the above thread and see if that works for you. You can so this by booting the live cd and mounting your partition and editting the file.

I've booted from the live CD and mounted sdb1 (this is the / partition that also contains /boot). My menu.lst has two kernel entries pointing to (hd0,0) - which is of course not correct. I've changed this to (hd1,1), but didn't see any improvement. The existing XP partition has also been detected, and has an entry in menu.lst pointing to (hd0,2) - this is where Boot Camp installed it.

> **cyberdork33 said:**
> ```
find /boot/grub/stage1
```
This should tell you the device that grub THINKS it is installed to.

At first I only got "Error 15: File not found", then I remembered to use "sudo grub" and got (hd1,1).
Looks good. To be on the safe side, I did the following too:
> root (hd1,1)
> setup (hd1,1)
Still nothing... =(

Something else that may be significant: OSX does not recognize the partitions on the second disk correctly. After login, I get a warning that the "inserted disk" could not be read. And instead of

- EFI (200MB)
- Linux / (25GB)
- Linux /home (73GB)
- Swap (5.5GB)
- FAT shared (133GB)

the Disk Utility shows

- Free space (25GB)
- "DISK1S3" (73GB) [MS-DOS (FAT)]
- Linux Swap (5.5GB)
- "disk1s5" (133GB) [Mac OS Extended (Journaled)]

Maybe I should just create all the partitions that I'm going to need for Ubuntu with the Disk Utility?

---

### Post by cyberdork33 on 2007-11-19
> **street spirit said:**
> - Free space (25GB)
- "DISK1S3" (73GB) [MS-DOS (FAT)]
- Linux Swap (5.5GB)
- "disk1s5" (133GB) [Mac OS Extended (Journaled)
Well that is not right... maybe you just need to sync the partition tables? It looks like it did not get the changes to the partition table on your second disk updated to the GPT.  In rEFIt choose the partition inspector (or something like that)...

In Ubuntu, at the commandline, you can do these commands to see the two 'types' of partition tables (MBR vs GPT):
This will read the entire GPT (what OSX should see):
```
sudo parted /dev/sda print
```This will read the MBR (what legacy items will see such as grub):
```
sudo fdisk -l /dev/sda
```*This works because fdisk cannot read GPT.

If you create the partitions with Disk Utility, you will just have to recreate them as you cannot create linux partitions.

---

### Post by street spirit on 2007-11-20
> **cyberdork33 said:**
> Well that is not right... maybe you just need to sync the partition tables? It looks like it did not get the changes to the partition table on your second disk updated to the GPT.  In rEFIt choose the partition inspector (or something like that)...

Yeah, that's what I've been thinking, but I didn't see a way to sync the 2nd disk. The rEFIt partition tool always showed me the GPT and MBR tables for the 1st dist, and told me that they were identical and that there was nothing to do.

I decided to give Disk Utility a try, and to put the /-partition (including /boot) on the first disk, to avoid any grub weirdness. The second disk would only hold the Linux swap partition, and a large shared FAT32 partition. So, my new partition scheme looks like this:

[LIST]
[*]sda1: EFI system, 210MB
[*]sda2: OSX Leopard, hfs+, 730GB
[*]sda3: Linux /, ext3, 108GB
[*]sda4: WinXP, ntfs, 161GB
[*]sdb1: EFI system, 210MB
[*]sdb2: Shared, fat32, 240GB
[*]sdb3: Linux swap, 5.5GB
[/LIST]

The install went well; I entered "(hda0,2)" as the place where grub should be installed. After the reboot Windows wouldn't load anymore, so I reinstalled it. There were two new entries in the rEFIt loader, one with a penguin icon labeled "boot Linux from" (sic), and one with a dummy icon labeled "boot legacy OS from HD". I tried to use the rEFIt shell to get this sorted out, but for some reason the shell crashes as soon as I enter it. Oh well. Both icons will (after a delay) get me to the grub screen - yay! The entries were all messed up though, they all referred to (hd0,0) and /dev/hda1. I booted from the live CD and fixed menu.lst: I put (hd0,2) and /dev/hda3 in, and removed the "quiet splash" kernel parameters for debugging. Rebooted, and loaded Gutsy without any problems!

So, to summarize:
- hosed Windows
- crashed rEFIt shell
- created an orphan rEFIt entry
- **but I've got a working triple boot system!**

All in all, setting this up was just about as tedious as I expected it would be, and it was well worth it. On the other hand, if that disk ever crashes, I'm going to be out of business for at least a day, so I will probably buy another identical 1TB disk and use it as 1:1 mirror. [any thoughts about which software can clone an entire disk, including MBR and GPT tables?]

> 
This will read the entire GPT (what OSX should see):
```
sudo parted /dev/sda print
```This will read the MBR (what legacy items will see such as grub):
```
sudo fdisk -l /dev/sda
```

GPT (parted):
```

Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size   File system  Name                  Flags
 1      20.5kB  210MB   210MB  fat32        EFI System Partition  boot
 2      210MB   729GB   729GB  hfs+         Untitled
 3      729GB   837GB   108GB  ext3         Untitled
 4      839GB   1000GB  161GB  ntfs         Untitled

Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system  Name                   Flags
 1      20.5kB  210MB  210MB   fat32        EFI System Partition   boot
 2      210MB   244GB  243GB   fat32        DOS_FAT_32_Untitled_2
 3      244GB   250GB  6227MB  linux-swap   Untitled

```

MBR (fdisk):

```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47ea47e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       88606   711522328   af  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3   *       88623      101756   105496360   af  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sda4          101979      121602   157619888    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d772d77

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          26      204819+  ee  EFI GPT
/dev/sdb2   *          26       29612   237650284    b  W95 FAT32
/dev/sdb3           29628       30385     6081316   82  Linux swap / Solaris

```

The MBR part still doesn't look quite right, but I'm afraid that changing anything might mess up one of the OSs.

---

### Post by cyberdork33 on 2007-11-20
> **street spirit said:**
> The MBR part still doesn't look quite right, but I'm afraid that changing anything might mess up one of the OSs.

Actually, it looks like everything matches correctly...

you likely have two refit icons that start grub because grub is installed in two locations (but using the same config on your linux partition). Unfortunately, I don't have a good way to get rid of one, you basically have to overwrite the bootcode wherever your unwanted grub is...

---

### Post by street spirit on 2007-11-20
> **cyberdork33 said:**
> Actually, it looks like everything matches correctly...

Then I'm not touching those partitions again, ever! ;-)
Thank you, Cyberdork33, you've been a great help.


PS: Just for the record (in case anybody else is googling for this and can't find any relevant results):
I get a few lines of warnings when my kernel boots:

```

Starting up ...
[  155.831061] PCI: 0000:00:03.0: class 600 doesn't match header type 01. Ignoring class.
[  155.831129] PCI: 0000:00:05.0: class 600 doesn't match header type 01. Ignoring class.
[  155.831181] PCI: 0000:00:06.0: class 600 doesn't match header type 01. Ignoring class.
[  155.831233] PCI: 0000:00:07.0: class 600 doesn't match header type 01. Ignoring class.
[  156.740997] i8042.c: no controller found.
Loading, please wait...

```

These disappear again and don't cause any trouble (that I could see); maybe they'll even go away after I apply the mactel patches.

---

### Post by cyberdork33 on 2007-11-20
> **street spirit said:**
> Then I'm not touching those partitions again, ever! ;-)
Thank you, Cyberdork33, you've been a great help.


PS: Just for the record (in case anybody else is googling for this and can't find any relevant results):
I get a few lines of warnings when my kernel boots:

```

Starting up ...
[  155.831061] PCI: 0000:00:03.0: class 600 doesn't match header type 01. Ignoring class.
[  155.831129] PCI: 0000:00:05.0: class 600 doesn't match header type 01. Ignoring class.
[  155.831181] PCI: 0000:00:06.0: class 600 doesn't match header type 01. Ignoring class.
[  155.831233] PCI: 0000:00:07.0: class 600 doesn't match header type 01. Ignoring class.
[  156.740997] i8042.c: no controller found.
Loading, please wait...

```These disappear again and don't cause any trouble (that I could see); maybe they'll even go away after I apply the mactel patches.

If you are not having issues, it is probably not a big deal, but you could file a bug or something on it if you really wanted.

---

