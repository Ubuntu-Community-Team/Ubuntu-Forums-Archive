---
title: "[SOLVED] Triple boot on a MacBook"
date: 2008-06-01
forum: Apple Hardware Users
---

### Post by tiagobt on 2008-06-01
Hello there!

I'm trying to install three operating systems on my MacBook: Ubuntu 8.04, Mac OS X Leopard and Windows Vista. Besides, I reckon it would be nice to have an extra partition where I could store my files, formatted as FAT32 or NTFS. In general, I've tried to follow the tutorial at [http://www.flickr.com/photos/foskarulla/2310220114](http://www.flickr.com/photos/foskarulla/2310220114).

First, I partitioned the disk using Mac's Disk Utility (booting from Mac OS X installation DVD). I created the following partitions:

0: EFI protected
1: Mac OS X (Mac OS Extended)
2: Windows Vista (FAT for the moment)
3: Ubuntu (FAT for the moment)
4: Storage (FAT for the moment)

Then, I installed Mac OS X on partition number 1. After that, I installer rEFIt under Mac OS and opened Partition Inspector. I found weird that a little bit of unallocated space was left between partitons 1 and 2, but I continued anyway.

I booted from Vista's DVD and installed it normally, formatting partition number 2 as NTFS. Then, I went back to Mac OS and ran Partition Inspector again, hoping it would synchronize the partion tables. Everything was fine. I had Mac OS X and Windows Vista and could choose between them using rEFIt.

It was time to install Ubuntu. I booted from the CD and ran the installer. I had to erase partitions 3 and 4, and then create three new partitions: one for Ubuntu, one for the swap space, and one storage. According to Ubuntu, my partition table became:

/dev/sda1: EFI (recognized as FAT)
/dev/sda2: Mac OS X (Mac OS Extended)
/dev/sda3: Windows Vista (NTFS)
/dev/sda4: Ubuntu (ext3)
/dev/sda5: Swap
/dev/sda6: Storage (FAT32)

(At this point, I had unpartitioned space left on three different spots. One of them is the unallocated space I mentioned before. The other two had exactly 0 MB. Is this normal?)

I decided to install GRUB on (hd0,2), which is supposed to be my Windows Vista partition. When I was done, I went back to Mac OS and ran Partition Inspector once again.

Now I'm able to boot Ubuntu and Mac OS from rEFIt, but Windows no longer works. Also, when I choose Linux in rEFIt, the GRUB menu appears. I thouht rEFIt was going to handle the booting process alone, so I don't really get what's happening.

What did I do wrong?

Thanks a lot,
Tiago

---

### Post by cyberdork33 on 2008-06-01
Follow this:
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

You are going to have issues because the MBR partition table (which windows is limited to) can only hold 4 entries. Thus, in:

1. EFI
2. OSX
3. Windows
4. Ubuntu Root
5. Storage

The storage partition would be inaccessible to Windows. There are a few options...

[LIST=1]
[*]Convert your disk to a typical MBR disk, then you can use many more partitions. To do this, you have to clone your OSX install to an external drive, then convert your Mac drive to MBR, and restore the OSX partition to where you want.
[*]Move OSX to 5th place. OSX doesn't care where it is located on the disk.
[*]Rebuild a custom MBR table. (I can't offer a lot of help with this, but it apparently can be done).
[/LIST]
rEFIt is not a bootloader, it is just a GUI for your Mac's EFI. Linux still requires a bootloader that can load the linux kernel into memory. You can turn the GRUB timer down in the config so that it only comes up for a second and you will rarely notice it.

When installing Ubuntu, make sure you install grub to the Ubuntu root partition and not the MBR (which is the default) otherwise you will go through GRUB for Ubuntu and Windows. This is done via the "Advanced" Buttong in the Ubuntu installer (near the end of the install configuration).

---

### Post by tiagobt on 2008-06-02
Thanks a lot. I have just a few more questions. :)

1. Apparently, the newest Disk Utility for Mac is able to handle MBR tables. Can I just use it instead of cloning and restoring the Mac OS installation? If I do that, will I no longer have to worry about a hybrid MBR/GPT table?

2. You told me I can have as many partitions as I want if I format the disk as MBR. But what about the 4 partitions limit? Am I supposed to create extended partitions?

3. I'm not sure what to do with the swap partition. Can I create an extra partition normally?

4. I read the tutorial for the MacBook Pro. Does it assume I already have a dual boot (Windows Vista + Mac OS X) using Boot Camp? I couldn't figure out when to create the storage or swap partitions.

I'm planning to use the following partition table now:

(0) /dev/sda1: EFI
(1) /dev/sda2: Windows Vista (NTFS)
(2) /dev/sda3: Storage (FAT32)
(3) /dev/sda4: Mac OS X (Mac OS Extended)
(4) /dev/sda5: Ubuntu (ext3)
(5) /dev/sda6: Swap

5. Does that work? Will the Ubuntu partition be accessible from Windows using Ext2 IFS?

I'm sorry for asking so many questions. I just don't want to redo the installation process once again.

Tiago

---

### Post by cyberdork33 on 2008-06-02
> **tiagobt said:**
> 1. Apparently, the newest Disk Utility for Mac is able to handle MBR tables. Can I just use it instead of cloning and restoring the Mac OS installation? If I do that, will I no longer have to worry about a hybrid MBR/GPT table?
If you convert it, you will not have to worry about a hybrid table. The issue is not with Disk Utility, it is the fact that Leopard will not install to a MBR disk.

> **tiagobt said:**
> 2. You told me I can have as many partitions as I want if I format the disk as MBR. But what about the 4 partitions limit? Am I supposed to create extended partitions?Yes. The hybrid table cannot use extended/logical partitions, but you can with a MBR-only disk.

> **tiagobt said:**
> 3. I'm not sure what to do with the swap partition. Can I create an extra partition normally? I am not sure what you are asking. You can create a swap partition with gparted.

> **tiagobt said:**
> 4. I read the tutorial for the MacBook Pro. Does it assume I already have a dual boot (Windows Vista + Mac OS X) using Boot Camp? I couldn't figure out when to create the storage or swap partitions. You have to be more specific about what you are are doing. after you shrink your OSX partition with Bootcamp or whatever, use gparted to create your other partitions.

> **tiagobt said:**
> I'm planning to use the following partition table now:

(0) /dev/sda1: EFI
(1) /dev/sda2: Windows Vista (NTFS)
(2) /dev/sda3: Storage (FAT32)
(3) /dev/sda4: Mac OS X (Mac OS Extended)
(4) /dev/sda5: Ubuntu (ext3)
(5) /dev/sda6: Swap

5. Does that work? Will the Ubuntu partition be accessible from Windows using Ext2 IFS?
No. Ubuntu would likely not even boot because it is the 5th partition, and Windows will not be able to see the Ubuntu partition because it is beyond #4. Your original plan would be fine if you converted to an MBR disk.

---

### Post by tiagobt on 2008-06-06
Hello again!

I decided to read the website in cyberdork33's signature (EFI-MBR Madness). I found the article pretty interesting. It cleared several questions I had. After that, I had second thoughts about converting the disk to MBR only. Besides having to clone my Mac OS X installation, I'd no longer be able to upgrade my firmware. Taking that into consideration, I decided to try and set up a hybrid EFI-MBR disk again.

I chose the following configuration:

(hd0,0) /dev/sda1 - EFI
(hd0,1) /dev/sda2 - Storage (FAT32)
(hd0,2) /dev/sda3 - Windows Vista (NTFS)
(hd0,3) /dev/sda4 - Ubuntu Linux (ext3)
(hd0,4) /dev/sda5 - Mac OS X (Mac OS Extended)
(hd0,5) /dev/sda6 - Swap (Linux Swap)

I installed Grub on (hd0,3) and I'm using rEFIt.

If I'm not mistaken:

- Windows will boot because it is among the four MBR partitions.
- Windows will be able to see the storage partition and Ubuntu because they are both among the four MBR partitions.
- Mac OS will not be visible in the MBR table, but this is not a problem.
- Windows will not be able to see Mac OS X, but this is not an issue to me, since I have a shared storage partition.
- Linux will be able to see all partitions because it can handle EFI/GPT.
- Grub will work because it is among the four MBR partitions.

The installation looked fine. I used Mac's Disk Utility to make the partitioning, and then installed Mac OS, Windows and Linux. Just after I installed Linux, Windows stopped working. The following error message is shown during boot (my translation):

> Windows was not successfully started. A recent hardware or software change may have caused the problem. To correct the problem:

1. Insert Windows installation disk and restart the computer.
2. Choose your language configuration and click "Next."
3. Click "Repair your computer."

In case you don't have the disk, contact the system administrator or the computer retailer to obtain assistance.

File: \Windows\system32\winload.exe
Status: 0xc000000e
Information: The selected entry could not be loaded because the application is missing or damaged.

I tried to follow the steps indicated, but the Windows Vista DVD did not even find my disk.

What did I do wrong this time?

Thanks once again,
Tiago

---

### Post by cyberdork33 on 2008-06-06
i'd say that the problem is that windows likes to be the last partition (i.e sda4). Some people have gotten it to work otherwise though.

---

### Post by tiagobt on 2008-06-06
I see. Then the following should work?

(hd0,0) /dev/sda1 - EFI
(hd0,1) /dev/sda2 - Storage (FAT32)
(hd0,2) /dev/sda3 - Ubuntu Linux (ext3) <- GRUB
(hd0,3) /dev/sda4 - Windows Vista (NTFS)
(hd0,4) /dev/sda5 - Mac OS X (Mac OS Extended)
(hd0,5) /dev/sda6 - Swap (Linux Swap)

---

### Post by cyberdork33 on 2008-06-06
exactly.

---

### Post by tiagobt on 2008-06-07
I tried the partition table above, but had no luck. Windows showed the same error message when I tried to boot. I also tried to reinstall Windows on the same partition (sda4), but the installer told me it wasn't able to install Windows on the partition I chose (even after I formatted it). Any ideas?

---

### Post by tiagobt on 2008-06-08
I think I know what the problem might be. When I ran gptsync.efi from the rEFIt menu, the MBR partition table was updated as follows:

```
Current MBR partition table:
# A   Start LBA   End LBA   Type
1        ...       ...      EFI Protective
2 *      ...       ...      FAT32 (LBA)
3        ...       ...      Linux
4        ...       ...      NTFS/HPFS
```

That is, the partition marked as active is number 2 (storage) instead of number 4 (Windows). I'm not sure what difference it makes, but I read somewhere that Windows should be the active partition. Is there a way to fix that?

Tiago

---

### Post by _alex_ on 2008-06-08
> **tiagobt said:**
> I also tried to reinstall Windows on the same partition (sda4), but the installer told me it wasn't able to install Windows on the partition I chose (even after I formatted it). Any ideas?

Seems like I ran into the same problem trying to reinstall Vista: [http://ubuntuforums.org/showthread.php?t=822146](http://ubuntuforums.org/showthread.php?t=822146)

If you figure out how to fix it, please let me know :D

---

### Post by tiagobt on 2008-06-08
> **tiagobt said:**
> I think I know what the problem might be. When I ran gptsync.efi from the rEFIt menu, the MBR partition table was updated as follows:

```
Current MBR partition table:
# A   Start LBA   End LBA   Type
1        ...       ...      EFI Protective
2 *      ...       ...      FAT32 (LBA)
3        ...       ...      Linux
4        ...       ...      NTFS/HPFS
```

That is, the partition marked as active is number 2 (storage) instead of number 4 (Windows). I'm not sure what difference it makes, but I read somewhere that Windows should be the active partition. Is there a way to fix that?

Tiago

I tried to boot Ubuntu and then set /dev/sda4 as the active partition using fdisk. Windows still shows the error message and Ubuntu no longer boots. Clearly not a wise thing to do...

---

### Post by tiagobt on 2008-06-08
I was reading the post [MacBook triple boot success!]("http://ubuntuforums.org/showthread.php?t=187465") and had another idea. According to the author, the partitioning tool used by Ubuntu (parted) understands GPT, but overwrites the MBR table created by Windows. He suggests backing up the MBR before installing Ubuntu and then restoring the backup later on. Do you guys think this might help?

I just find weird that this problem never happened when I dual-booted a regular PC (Windows + Ubuntu). But I might give it a try.

---

### Post by cyberdork33 on 2008-06-08
My OSX partition is the active one on my iMac (but I am not trying to use Windows).

---

### Post by tiagobt on 2008-06-15
Cyberdork33,

You're right. The active partition doesn't make a lot of difference. Apparently, it changes whenever you boot a new operating system.

I finally got the triple boot working. The MBR backup seemed to do the trick. Ubuntu somehow messes up the MBR, causing Windows to stop working.

In case someone has the same problem, the procedure is the following:

1. Boot Ubuntu's live CD and make a backup of the MBR before installing the operating system:

```
sudo dd if=/dev/sda of=/tmp/sda.mbr bs=512 count=1
```

2. The backup will be placed in the /tmp folder. I recommend you copy this file to a safe place (for example, an external drive).

3. Install Ubuntu normally, placing GRUB on the Linux root partition.

4. When the installation is done, restore the backup:

```
sudo dd if=/tmp/sda.mbr of=/dev/sda
```

This should work.

Cyberdork33, thanks again for all the help!

Tiago

---

### Post by cyberdork33 on 2008-06-15
glad to help, please mark as solved

---

