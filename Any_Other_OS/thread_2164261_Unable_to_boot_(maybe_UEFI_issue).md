---
title: "Unable to boot (maybe UEFI issue)"
date: 2013-07-30
forum: Any Other OS
---

### Post by mbnoimi on 2013-07-30
I was using Ubuntu 12.10 (Mint 14) without any problem. I decided to format system partition (ext4) and install the recent Ubuntu 13.04 (Mint 15) for that I did the following but all of these ways didn't install Ubuntu and I'm right now stuck with LiveDVD and talking to you though it :roll: So may you please response ASAP:

1) Booted from LiveDVD though legacy boot source and chose SATA2: [http://imgur.com/ws8gtSm](http://imgur.com/ws8gtSm)
2) Formatted and Installed the system by using this disk setup: [http://imgur.com/1YSvMPB](http://imgur.com/1YSvMPB)
3) After restarting process and remove LiveDVD my PC couldn't see any boot source?!

I tried another way by re-booting from UEFI source:
1) Booted from LiveDVD though UEFI: hp CDDVDW boot source: [http://imgur.com/ws8gtSm](http://imgur.com/ws8gtSm)
2) Formatted and Installed the system by using this disk setup: [http://imgur.com/OKSaxhG](http://imgur.com/OKSaxhG)
3) Before restarting process I got error message told me that Mint failed in grub-efi: [http://imgur.com/r1NZzTT](http://imgur.com/r1NZzTT)

I tried another way by re-booting from UEFI source:
1) Booted from LiveDVD though UEFI: hp CDDVDW boot source: [http://imgur.com/ws8gtSm](http://imgur.com/ws8gtSm)
2) Formatted and Installed the system by using this disk setup: [http://imgur.com/N6sNzCh](http://imgur.com/N6sNzCh)
3) After restarting process and remove LiveDVD my PC couldn't see any boot source?!

I made another trial
1) Rebooted my PC for clean strart up and booted through legacy source (LiveDVD)
2) Formatted and Installed the system by using this disk setup: [http://imgur.com/cJJQcEd](http://imgur.com/cJJQcEd)
3) Installed and run boot-repair which told me that it successfully repaired my system and I've to reboot
4) After restarting process and removing LiveDVD my PC couldn't see any boot source?!

P.S. In case I removed the LiveDVD my boot menu appears as following: [http://imgur.com/WImw2vI](http://imgur.com/WImw2vI)

---

### Post by oldfred on 2013-07-30
Moved to Other os since Mint.

I do not know Mint, but how you install with BIOS and MBR partitioning and UEFI with gpt partitioning are a lot different. If drive is already MBR then your UEFI install will not work. (And vice-versa.)

       Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

 Install with screen shots:
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT)

I do not know what details may make Mint different.

---

### Post by mbnoimi on 2013-07-31
> **oldfred said:**
> I do not know what details may make Mint different.
It hasn't much differnce, Ubuntu is parent of Mint

> **oldfred said:**
> but how you install with BIOS and MBR partitioning and UEFI with gpt partitioning are a lot different. If drive is already MBR then your UEFI install will not work. (And vice-versa.)
No I didn't do that, I just made some sperated trials (maybe I wasn't clear). Any way In the following parted -l result. May you please guide me what I've to do becasue I gave up and will stop my trials (UEFI help page doesn't help me very much)?
```

mint archives # sudo parted -l
Model: ATA Hitachi HDS72105 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End    Size   File system  Name  Flags
 4      100GB  500GB  400GB


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

mint archives # 

```

P.S. You can guide me to use parted or GParted too.

---

### Post by oldfred on 2013-07-31
Drive is now gpt, to install with UEFI you need several partitions. You can also install Ubuntu to BIOS boot with gpt partitioning, but Windows will only boot from gpt partitioned drives with UEFI, if you are thinking of Windows also. I prefer separate drives anyway.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

I do not use a separate /home as I have multiple installs and want the data in every install. So I leave /home inside my / (root) but create large data partition(s) and link those partitions back into /home so it looks like a normal /home. My 25GB / uses about 9GB wtih lots of apps, and about 2GB is /home and 1.5GB of that is .wine for Picasa as I have not moved that to my data partition.

---

