---
title: "GPT and MBR partitioning confusion"
date: 2012-06-13
forum: Apple Hardware Users
---

### Post by skullmunky on 2012-06-13
I'm having some issues with the partitioning on my triple-boot Macbook Pro and could use some help massaging the GPT and MBR partition tables.

Now full disclosure, the end goal that I need to achieve is actually just to re-install Windows, everything else is working beautifully - but please let's overlook that little fact and focus on the technical issue at hand :lolflag: 

The basic problem is that my WinXP install is kerput - infected with viruses, can't boot it through refit or GRUB, and in any case it's time I replace it with W7 so it's slightly less horrible.  Windows 7 installer doesn't recognize the NTFS partition I have that currently contains XP, thinks it is blank space, won't install, and won't create any more partitions because it thinks there are too many.  braindead thing. 

Here is my curent setup:

MBP 6,2
Triple boot, OSX 10.6, Kubuntu 12.04, Windows XP 32

Here is what rEfit's partitioning tool sees:

Current GPT Partition Table:

1        40        409639  EFI System (FAT)
2    409640     451297319  Mac OS X HFS+
3 451299328     879116287  Basic Data       <- ext4, Kubuntu
4 879116288     957241343  Basic Data       <- NTFS, Win XP
5 957241344     976771071  Linux Swap

Current MBR Partition Table:

1           1         39  EE  EFI Protective
2          40     409639  0B  FAT32 (CHS)
3      409640  451297319  AF  Mac OS X HFS+
4 * 451299328  879116287  83  Linux

Status: Analysis inconclusive, will not touch this disk
Error: Not Found returned from gptsync.efi

What looks odd to me is that the MBR has that extra FAT32 partition in between the EFI and the HFS+.  I feel like it should look more like:

1           1     409639  EE  EFI Protective
2      409640  451297319  AF  Mac OS X HFS+
3   451299328  879116287  83  Linux
4   879116288  957241343  07  NTFS

But how do I make that happen ... ?


For background, in case it helps, you may be wondering how the heck it ended up in this state.  I've had the triple boot working flawlessly for a couple years on this machine (the whole setup went very smoothly, actually).  I ran into problems because the XP partition got itself infected with the TDSS rootkit, which infected the MBR.  I used Kaspersky's TDSSKiller to remove it, which worked, I guess, but of course wrecked the hybrid GPT/MBR partition table so I couldn't boot the linux or windows partitions anymore.  After a whole lot of poking at it I got an MBR that worked well enough that I could reinstall Kubuntu, let it re-install GRUB, and can now boot the linux partition again, which is the most important one for me :D  But I do need to get the Windows one working too.  So thanks in advance for any help.

And yes, obviously the better solution would be a VM or Wine for the occasional windows stuff I need to run, but I need full hardware 3D acceleration for them and the Wine support is good but not quite perfect just yet.  So 'til then, gotta fix this MBR.

---

### Post by skullmunky on 2012-06-13
Oh nos, it got worse.  

While working out a plan for rebuilding the MBR, I figured one step I should do anyway is zero and reformat the NTFS partition (currently Windows XP, named "BOOTCAMP", partition #4).  I did this using Apple's Disk Util.  It did reformat, but now look at what it did to my partition table:

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  Basic Data
 2         409640    451297319  Mac OS X HFS+
 3      451299328    879116287  Basic Data
 4      879116288    879525887  EFI System (FAT)
 5      879525888    956979199  Basic Data
 6      957241344    976771071  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1    976773167  ee  EFI Protective

(1) is supposed to be the EFI system.  
(2) is the OSX partition
(3) is the ext4 Linux partition
(4) was created by Disk Utility without my asking it to :confused:
(5) is NTFS, which I'm going to reinstall Windows on

Now I don't have a hybrid GPT/MBR table anymore, which I assume is ok since either rEfit can recreate it for me or I can construct it by hand using fdisk (or something...?) 

I think I need to do these steps:

1. return 1 to being EFI
2. get rid of 4 and merge it with 5 to create new NTFS partition
3. sync GPT and MBR 
4. enjoy some iced tea 

But how do I do that?

And in the process of shifting the EFI partition around can I make the machine totally bricked?

---

### Post by oldfred on 2012-06-13
I do not know Macs.

But efi partitions are supposed to be the first partition. A non-Apple user did install with the FAT partition second, but I think the issue is a FAT driver cannot read beyond a certain point on a drive, so it is easiest just to tell us to make it first to avoid issues.

With Windows & a Mac you have to have the hybrid and have to keep them in sync or you will have major issues.

[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

---

### Post by skullmunky on 2012-06-19
Fixed it! 

- Used gdisk to remove GPT partitions (4) and (5), and changed the type of partition 1 back to EFI

- Created a new partition (4) as NTFS

- Used fdisk to manually write the MBR partition table in the correct scheme, entering the correct start block and size for each

- OSX and Kubuntu boot fine

- Installed Windows 7 onto partition 4, installed Boot Camp drivers for it, everything works fine.  Doing this didn't seem to impact the other bootloaders, so I didn't need to reinstall GRUB or anything - all 3 boot directly from the rEfit menu now.  Hooray!

---

### Post by YannBuntu on 2012-06-20
Please could you indicate your current [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1")? (this will not change your boot)

---

