---
title: "Partitions broken?"
date: 2008-01-24
forum: Apple Intel Users
---

### Post by smocksturr on 2008-01-24
Okay, so, after a failed attempt at triple booting, I nuked all partitions except the EFI boot and my Mac partition, 89 gigs.
I decided to boot camp windows again to begin the attempt. I turned the date back to use the assistant (still on Tiger) and it informed me that it wouldn't work unless there already was a boot camp partition or the disk was all Mac.
So, I booted off my external backup and tried to add in a new partition on my main drive to put windows on.
I can make an "MS-DOS" partition with Disk Utility (well, first an HFS part with iPartition then changed to fat32 with disk utility) but Windows install won't recognize it.
Even GPARTED recognizes the partition, even as a fat32 partition.
Is there a way I can 
a)restore my drive to all Mac without reformatting so that I can use boot camp
or
b)create a fat32 partition windows will recognize?

---

### Post by cyberdork33 on 2008-01-24
remove all the other partitions (as in just free space left) and Boot camp will let you shrink the OSX partition. after you shrink it (and create a windows partition) of a very small value, then you can reboot and run bootcamp again to "restore" the mac partition (but it will actually stretch it to the rest of the free space).

---

### Post by smocksturr on 2008-01-25
Okay, I'm still trying to make this triple boot work so I didn't restore the partition.
I boot camped windows back on and then installed Ubuntu on the last partition.
I even made sure the bootloader was installed on the Linux partition, not on the MBR.  Even then, windows gives me HAL.DLL error.
Tried using recovery console and fixmbr, no dice.
Tried syncing tables with rEFIt, no dice.
I'm close to giving up.

---

### Post by cyberdork33 on 2008-01-25
> **smocksturr said:**
>   Even then, windows gives me HAL.DLL error.
Tried using recovery console and fixmbr, no dice.
Tried syncing tables with rEFIt, no dice.
I'm close to giving up.Those tools will not fix that error. The problem is that windows does not like that the setup on the hard drive changed after it was installed. Windows is getting to the boot process, but stops, because of the hall.dll error. If editting the boot.ini file to match the correct partitions does not work, then I don't know what else to tell you. 

Are you putting the windows partition last on the disk?

What does your partition layout look like? ```
sudo fdisk -l /dev/sda
```

What does your boot.ini file look like?

---

### Post by smocksturr on 2008-01-25
I can't get the wifi to work in Ubuntu yet, so no fdisk, but here's my boot.ini:
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


Also, here's my disk setup:
sda1:EFI boot
sda2:Mac HD
sda3:Windows FAT32
sda4:Ubuntu
sda5:Swap

---

### Post by cyberdork33 on 2008-01-25
> **smocksturr said:**
> Also, here's my disk setup:
sda1:EFI boot
sda2:Mac HD
sda3:Windows FAT32
sda4:Ubuntu
sda5:SwapThe fdisk command shows the partition entries in the MBR exactly. That is why I was asking for that output. If the above matches, then I think you are OK, but I would make 100% sure that is what shows in the MBR. If that is the case, it may be because Ubuntu is in partition 4 and not windows. Windows likes to be last for some reason. I think the boot.ini is right for the setup you have now.

---

### Post by smocksturr on 2008-01-26
Okay, used fdisk on my gparted livecd
just like I thought:
sda1: GPT EFI boot
sda2: Unknown (HFS+)
sda3:win32 fat
sda4:Linux


So, if I were to nuke all partitions except mac and EFI, how could I go about making Windows the last partition?
When I boot camp, the drive becomes 2, 90 gigs mac, 25 gigs windows.
How can I shrink the windows drive so there is space before it?
Can that be done with gparted as well? (i have the feelin that you can now that I think about it)
So. If I delete my linux partition, move my Windows one the end of the drive, and reinstall Ubuntu before windows, you think that may help?
Install the bootloader to sda3 (which will then be Linux) /hda(0,2)?
And then run fixmbr from the Windows cd?

---

