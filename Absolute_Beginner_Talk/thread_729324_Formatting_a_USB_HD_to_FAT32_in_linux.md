---
title: "Formatting a USB HD to FAT32 in linux"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by apokkalyps on 2008-03-19
I have a maxtor 750gb external drive that I want to use on both Ubuntu and XP.  It came with an NTFS file system on it.  The problem with that is that linux seems to only half support NTFS.  Windows XP doesnt seem to give the option to 'Eject' an external HD the way it does other removable media like thumb drives.  
So all I can do is just unplug the drive which leaves some flag set (NTFS in use) and then linux won't mount the drive (because it hasnt been unmounted properly).  I can do "sudo mount ntfs-3g /dev/sdg /media/disk -o force" but that only half works, sometimes it will unset that flag, but usually it wont actually mount, and ill have to do that command several times and then unplug it and plug it back in and hope it mounts automaticly.  Sometimes it works, sometimes it doesnt, but I definatly dont want to deal with that crap indefinatly.
So I've pulled all the data off of it, and my plan is to put a FAT32 file system on the disk, so there are no "in use" flags to deal with.  I don't see what the point of that stupid flag is anyway.  I thought about making a script that would just unset the flag immediatly and then try to do the mount, but im not too savvy with that and its buggy enough already.  Plus it defeats the purpose of the flags existance, (whatever that purpose is).  But I digress...

Windows refuses to format a volume bigger than 32gig to FAT32.  I have read that regardless of this windows can read much larger fat32 partitions than 32gig, and the actuall maximum FAT32 size is about 2TB.

Try 1:
So I'm trying to format a drive to fat32 in linux.  First tool i tried was:
# sudo mkdosfs -F 32 /dev/sdg -I
(it makes me use -I or it doesnt work, but I dont understand what this flag does)

This creates a partition that is readable in linux, but is actually a vfat partition (or does the disk properties in gnome always call fat partitions vfat?), and even tho supposedly windows can read vfat...it can't.  It just doesnt mount in windows.  It wont even give it a drive letter.

So I think I have to make it a traditional FAT32 filesystem.

Try 2:
Then someone on IRC turned me onto cfdisk, and I used this to delete the current partition and put a new one on that was FAT32 (NOT LBA).  Primary, non-bootable.  It calls the filesystem "W95 FAT32" even though I thought I remembered FAT32 came out with Win98.
So that seemed to work when i wrote it, and I still had access to the blank drive after that and could put a new folder in it, but when I unplugged it and plugged it back in, now it won't mount anymore (automaticly).  Also disk properties in gnome still listed FS as vfat, so who knows what was going on there.

I've also tried gparted and it gave me an nondescriptive error when I tried to write that fat32 partition.

I'm out of ideas here, can someone please help?  Thanks

---

### Post by Diabolis on 2008-03-19
mmm gparted is the best tool for this, but seems like your hd is about to be useless. Doing those hard plug ins/outs usually break drives. That happened to me with a 2gb usb stick. It would be helpful if you post the error that gparted returned. Maybe you need to check the disk for errors with **fsck**. gparted has a option that will check the disk for errors too.

---

### Post by louieb on 2008-03-19
> **apokkalyps said:**
> ..  Windows XP doesnt seem to give the option to 'Eject' an external HD the way it does other removable media like thumb drives.  

Weird: XP should have a safety remove hardware   icon in the notification area.  
Think thats the 1st thing I would try to get fixed.  
Did this search [http://www.google.com/search?q=safety+remove+hardware]("http://www.google.com/search?q=safety+remove+hardware+icon&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a")

and found this: [http://www.worldstart.com/tips/tips.php/2807](http://www.worldstart.com/tips/tips.php/2807) could be something simple.

> "W95 FAT32" even though I thought I remembered FAT32 came out with Win98It came out with Win95 thats when long file names became available in Windows.  vfat is just another name for fat32 before that we were stuck with fat16 and 11 character file names in DOS.  

Just not much help with making a fat32 file system on your drive.  
[IMG]http://louboldt.com/ptwocents.gif[/IMG] Really doesn't matter what file system you use.  Always a greater chance of something going wrong  if it doesn't get closed out properly.
Good luck.

---

### Post by apokkalyps on 2008-03-19
I checked that link and I think i figured out how to safely remove hardware in XP.  I wasn't using that Icon in the system tray.  I was just trying to right click the drive in my computer.  For thumb drives it gives me an eject option right there, but i guess not for HDs.


But, im still interested in why this isn't working.  I found where gparted was putting its error message and I saved it as htm.  

Here:
> 
GParted 0.3.3

Libparted 1.7.1

Delete /dev/sdg1 (fat32, 698.64 GiB) from /dev/sdg  00:00    ( SUCCES )
     	
calibrate /dev/sdg1  00:00    ( SUCCES )
     	
path: /dev/sdg1
start: 0
end: 1465149167
size: 1465149168 (698.64 GiB)
delete partition  00:00    ( SUCCES )

========================================

Create Primary Partition #1 (fat32, 698.64 GiB) on /dev/sdg    ( ERROR )
     	
create empty partition  00:01    ( ERROR )
     	
path: /dev/sdg1
start: 0
end: 1465144064
size: 1465144065 (698.64 GiB)
libparted messages    ( INFO )
     	
Unable to open /dev/sdg - unrecognised disk label.

========================================


edit:
also I ran 
> fsck /dev/sdg

and it spit out
> barrett@barrett-desktop:/usr$ fsck /dev/sdg
fsck 1.40.2 (12-Jul-2007)
de2fsck 1.40.2 (12-Jul-2007)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdg

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


---

### Post by louieb on 2008-03-20
Their both giving the same error. The **disk label **is another name for the **partition table**.  GParted has an option to put in a new disk label. Think thats the first thing I would try.  New disk label then create partition. 

If that doesn't work then I'd go to the Maxtor (Seagate bought Maxtor) website and see what diagnostic software they have available.

---

### Post by apokkalyps on 2008-03-20
Ok this just gets wierder and wierder.  So I reformatted with gparted and it was successful.  No erros.  Yet, when I browse onto it I can't do anything on the drive through the file browser.  I cant make a directory.  I CAN save a text file through gedit.  But I cannot delete it in the file browser.  When I unmount and plug it into xp.  It comes up and says "cannot format H:", rather than saying "h: is not formatted, would you like to now".  This doesn't make sense at all....

---

