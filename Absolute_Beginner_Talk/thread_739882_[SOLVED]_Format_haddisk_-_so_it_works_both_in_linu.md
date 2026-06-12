---
title: "[SOLVED] Format haddisk - so it works both in linux and windows ?"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by Sceiron on 2008-03-30
I have an old 2,5" Harddrive for an old laptop. I have put this HD in an external-USB cabinett (so i have a external USB disk). I want to format it so i can access the data on it in both windows and linux. This disk is attended to be a media-storage disk.

First Ii formated the Harddrive in windows with NTFS, result:
Disk woring in windows. Disk had to be forcemounted in Linux, so i was able to access the disk in ubuntu, but the "Media data" did not come up. (I put a video on it to do a test).

Second atempt, i formated the disk to FAT 32 in windows:
Same result as above, but the disk says its has no space for storing media in windows.

Third attempt:
I formated the disk using fdisk making the fs ext3, but noe the disk would not come up in windows.
I have found out that there is made some programs that would get my disk up in windows, but this is not whats i wnat.

what i need help with:
I want the disk formated so i will show up i both linux and windows ?

That sound so easy, doenst it :lolflag:
(but not for me)

---

### Post by c-ron on 2008-03-30
Format it again with Ext2 (NOT Ext3) so you can use *nix permissions on it.
In Windows, install the Ext2 Installable File System: [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

PS: Awesome King Crimson avatar!

---

### Post by Tux Aubrey on 2008-03-30
The answer is b) FAT32 ("vfat"), so I don't understand why it didn't work for you.  You can also get reasonably reliable support for reading and writing NTFS drives in linux, but I still thinkvfat is safer.

Whenever I set up a dualboot machine, I usually have a vfat partition to allow "seamless" data exchange between the two OS's.  Most external usb storage is already formatted as FAT32 which is why they plug n'  play so well with Linux and Windows.

Have another try.

FAT16 should also work.

---

### Post by bumanie on 2008-03-30
I have an external 2.5" hdd in an external case. It works fine in both windows and ubuntu when formattd to FAT32. If you had a video file larger than 4gb, that will be your issue because FAT32 cannot deal with files larger than 4gb, that's why windows changed to ntfs, once video  became common place.

---

### Post by Sceiron on 2008-03-30
> **c-ron said:**
> Format it again with Ext2 (NOT Ext3) so you can use *nix permissions on it.
In Windows, install the Ext2 Installable File System: [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)
I dont wanna do this, cause its a disk i'll be bringing with me around, so im not so keen on installing this on my friends machines etc...
> 
PS: Awesome King Crimson avatar!
:D

---

### Post by Sceiron on 2008-03-30
> **bumanie said:**
> I have an external 2.5" hdd in an external case. It works fine in both windows and ubuntu when formattd to FAT32. If you had a video file larger than 4gb, that will be your issue because FAT32 cannot deal with files larger than 4gb, that's why windows changed to ntfs, once video  became common place.

Hey, this is infact the problem, i put a blueray hd-dvd file on it, tnx for that info dude.
Is there any clever way to solve this?

---

### Post by Sceiron on 2008-03-30
> **Tux Aubrey said:**
> The answer is b) FAT32 ("vfat"), so I don't understand why it didn't work for you.  You can also get reasonably reliable support for reading and writing NTFS drives in linux, but I still thinkvfat is safer.

Whenever I set up a dualboot machine, I usually have a vfat partition to allow "seamless" data exchange between the two OS's.  Most external usb storage is already formatted as FAT32 which is why they plug n'  play so well with Linux and Windows.

 Its not a dualboot machine. But Fat 32 will not be the solution because of the filesice, se above post :)

But on the other hand, i may have done something wrong formatting the HDD. When i run fdisk -l in CL, i get senseful information about the disk, but it also says:
> 
Disk /dev/sdb doesn't containt a valid oartition table
Did i format it wrong using fdisk? 
here is what i did:
```
 fdisk mkfs -t ext3 /dev/sdb
```

---

### Post by ugm6hr on 2008-03-30
NTFS is probably what you want.

If formatted NTFS in Windows, it should "just work" in Ubuntu, as long as you have Gutsy or later (as suggested in your info).

It should not need to be "force mounted" (I don't know what that means).

I have a NTFS USB HD which works fine in Ubuntu, as does another one with 2 partitions (fat32 & ext3).

---

### Post by bumanie on 2008-03-30
The above is correct, it slipped my mind that from gutsy onwards ntfs-3g is included natively (I only recently changed to gutsy as it worked poorly on my old computer). Ntfs-3g allows ubutnu to natively read/write to ntfs.

---

### Post by Sceiron on 2008-03-30
> **ugm6hr said:**
> NTFS is probably what you want.

If formatted NTFS in Windows, it should "just work" in Ubuntu, as long as you have Gutsy or later (as suggested in your info).

It should not need to be "force mounted" (I don't know what that means).

I have a NTFS USB HD which works fine in Ubuntu, as does another one with 2 partitions (fat32 & ext3).

Okey, gave it another try. I used the Gparted-live CD to reformat it to NTFS. The disk is now working in windows. But when i plug it into my linux-machine i get the following error. see attachement.

Im using Ubuntu Gutsy Gibbon, yes.

---

### Post by bumanie on 2008-03-30
That mesasge indicates that you removed the drive from windows without going through the 'safe removal' routine. Ubuntu is seeing the file system as in use as it hasn't been shut down correctly. Linux will not mount the drive until the drive is shut down correctly. Therefore, activate the drive in windows again and ensure you go throught the correct 'safe removal' routine. It should then work in ubuntu.

---

### Post by Sceiron on 2008-03-30
> **bumanie said:**
> That mesasge indicates that you removed the drive from windows without going through the 'safe removal' routine. Ubuntu is seeing the file system as in use as it hasn't been shut down correctly. Linux will not mount the drive until the drive is shut down correctly. Therefore, activate the drive in windows again and ensure you go throught the correct 'safe removal' routine. It should then work in ubuntu.

Oh, damn, what to do about "me"  ...arg
Thank you for the explanation.
What is the proper command in CL for unmounting the disk, now im thinking about unmounting in linux.
Think my problems are solved now, disk shows up in windows and linux. Will test a media file asap!

Thanks all !

---

### Post by Sceiron on 2008-03-30
Everything is working, woho 
The issue was, hm, me, and not the disk itself :lolflag:

Thanks again.

---

### Post by bumanie on 2008-03-30
To unmount in ubuntu either right click th edevice icon on the desktop and left click unmount device.

---

### Post by niteshifter on 2008-03-30
ntfs-3g is indeed pretty handy but let's all do remember it's not quite perfect. Problems can arise if Windows has compressed files or if has encrypted files / folders. The latter will affect almost no one, but compression can be a problem for anyone. It depends upon the particular volume being used.

I personally trust it 100% for reading, for writing - not so much. Safer to roll the file thru a FAT file system first, then let windows copy from that into a NTFS volume. That having been said, when I've had problems was when the NTFS volume is nearly full, all files are compressed, or has errors.

FAT32 does indeed have a 4GB limit on file size. One gets around this by splitting the file into chunks less than 4GB (use the split command in Linux), copy them over, then combine them
```
copy /B  file-part-1 + file-part-2 + file-part-N  destination-file
```
in a CMD.EXE session in windows. The /B tells COPY these are binary files.

Since I'm a stickler for historical accuracy, NTFS was introduced in 1993 - well before video became poplular. Microsoft rolled it out with Windows NT in order to provide a file system that supports file metadata, journaling and access control, among other things.

---

