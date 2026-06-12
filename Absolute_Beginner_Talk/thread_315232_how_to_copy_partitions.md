---
title: "how to copy partitions?"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by moshuptrail on 2006-12-08
I need to replace a hard drive, and I was thinking the easy way would be to just install the new drive as a second HD and then copy the partitions from the old drive to the new drive. Then remove the old drive and configure the new drive as the first HD and boot from it.

The old drive consists of:
hda1: 6Gb Windows Restore fat32
hda2: 30Gb Windows XP NTFS
hda5: 10Gb Ubuntu / ext3
hda6: 1Gb Linux swap
hda7: 30Gb /home ext3

The new drive has a lot more space so I could enlarge partitions after copying.  

Advice?  Is there a different way?  What utilities should I use?

---

### Post by aysiu on 2006-12-08
I don't know if there's a way to copy an entire hard drive, but you can copy each partition one by one using *dd_rescue* (the command is *dd_rescue*, but the package name is *ddrescue*--don't ask me why) or using PartImage.

**dd_rescue** ```
sudo dd_rescue -v /dev/hda1 /dev/hdb1
```

**PartImage**
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by PapaNerd on 2006-12-08
My preferred methodology would be to do a "clean" install of the OS with the new drive as the only drive in the machine, and then mount the old drive and copy your data into the new partitions.  Yes, this takes a bit longer on the initial re-build, but could easily save you countless hours debugging a potential configuration problem if things don't go right.

---

### Post by moshuptrail on 2006-12-08
I'm inclined to agree that it would be cleaner.  But there's a lot of "crap" that would need to be re-installed on the XP system. Not the least of it would be dozens of updates (each requiring a reboot ](*,) ) It might take a very long time.  Also I would still need to copy the recovery partition first.  And then there's no telling how Micro$oft will treat the new installation.

Re-installing Ubuntu (Xubuntu on this machine) will be much faster.  So I'm not worried about that.  Even copying the ext3 partitions will be easy.

Unfortunately I still need that horrible XP thingy.
There are a couple of programs that I just can't replace yet.

---

### Post by aysiu on 2006-12-08
From PartImage's webpage: > The NTFS (Windows NT File System) is currently not fully supported: this means you will be able to save an NTFS partition if system files are not very fragmented, and if system files are not compressed. In this case, you will be able to save the partition into an image file, and you will be able to restore it after. If there is a problem when saving, an error message will be shown and you won't be able to continue. If you have successfully saved an NTFS NTFS partition, you shouldn't have problems as you restore it (except in the case of bugs). Then the best way is to try to save a partition to know if it is possible. If not, try to defragment it with diskeeper or another tool, and try to saving the partition again.

---

### Post by PapaNerd on 2006-12-08
Yes, I know Windoze is a pain to reinstall as I just went through that converting my daughter's machine to dual boot (she wanted to access some of the non-unix games).  Had to buy a small 2nd drive for XP as it would freeze after the Ubuntu install, but work if I copyed in the pre-ubuntu MBR.  Found a dumb KB article on the Microsoft website acknowledging, but not solving, the problem.

My concern in your situation would be that copying XP over to the new drive may not work correctly if a different driver is needed for it to run off the new drive,  Obviously, this is avoided if you do a clean install.  However, it couldn't hurt to try the copy method first as you can always recover by doing a clean install afterward.  

Hints:  If you do need to install a fresh copy of XP, download all the patches you will need onto the old drive before you begin work on the new drive.  Intruders can compromise a new Windoze installation faster then the updates can be downloaded.  Also, only one reboot of XP is needed at the end of your updating process.  Just minimize the forced reboot messages and ignore them until the end.

---

### Post by moshuptrail on 2006-12-10
Of course, the chicken-s**t way to do this is simply to leave Windows XP in place and install Ubuntu on the new drive.  So far, the NTFS partitions are not showing signs of bad blocks.  Only the linux partitions that I added in previously unused sections of the HD.  Is it possible that NTFS is hiding problems?

Anyone know how to list the bad-block status of a partition? That is, how many?  I would guess it's different for NTFS and ext3.

```
Current Config:
hda 80G = 
   hda1 ntfs 6G
   hda2 ntfs 30G
   hda5 linux swap 1G
   hda6 ext3 linux / 10G
   hda7 ext3 linux /home 30G
new HD
hdb 200G (possible config)
   hdb1 unused 40G (leave room for XP later)
   hdb2 linux swap 1G
   hdbx ext3 linux / 10G
   hdby ext3 linux /home all the rest

```

---

### Post by bulldog on 2006-12-10
As far as I know,windows is capable to write around bad sectors so you won't notice they're there.

Bud it's along time ago when I was fiddling with XP,but if I remember correctly,there was a possibility to migrate windows to another disk.
This way all your apps and settings would be preserved.

But I can be mistaken about that..........but I remember something.......:D

---

### Post by smoker on 2006-12-10
you can usually download an app from the harddrive manufacturers website that can copy all info/partitions from the old to the new disk, this is by far the easiest way.

check the website of the hard drive maker

---

### Post by moshuptrail on 2006-12-10
The utility, MaxBlast4, is a piece of crap.  It boots up and recognizes the CD it just booted from as a floppy.  Then it proceeds in DOS mode.  It displays the new Maxtor drive on one screen, and on the the next screen it says it can't find a Maxtor drive to do the requested operation.  Must be some un-tested windows crap :D . 

Anyway, I was excited when I saw the CD in box and the features it boasted, but that turned to dissillusionment quickly.

I have already got the new drive partitioned and ready using the Gparted Live CD, which works just fine, thank you.

Next step will be to try to copy the old partitions using dd_rescue. (Thanks aysiu)  That seems like the best choice.  If successful, I'll leave a final post with details.

---

### Post by smoker on 2006-12-10
> have already got the new drive partitioned and ready using the Gparted Live CD, which works just fine, thank you.

why dont you use the gparted partition copy feature then?

---

### Post by moshuptrail on 2006-12-10
The what?
I didn't see one!  Is there one there?

Just the same, the reason for using dd_rescue is to be able to skip bad blocks.  It's running now and finding a lot more bad blocks than I thought were there.  But it's taking a real long time.  Most other utilities just drop dead when they hit a bad block.

---

### Post by moshuptrail on 2006-12-11
Here are some final answers:

1. As stated above, I used Gparted Live CD to partition the new drive
2. I think you need to unmount the partitions before using dd_rescue.  At any rate, that worked for me.  I simply clicked on System > Administration > Disks.  Click the partitions tab, and on the partitions you want to un-mount, click the "Disable" button.
3. I ran the command as follows:
 > sudo nice dd_rescue -v /dev/hda1 /dev/hdb1
The nice command runs it at a lower priority so you can hopefully go on with some other work while it's running.  Yes, you can run it right from a terminal with Ubuntu running.
4. the dd_rescue took 5-12 hours depending how many bad blocks it found and the size of the partition.  Upon finding a bad block it seems to reduce its block size and re-try in an attempt to localize any damage to the nearest 512 byte block.  The hard drive itself seems to "lock up" the computer when it stumbles on a bad block.  I think the hardware is doing some re-tries of it's own. However this prevents the drive from doing any other work for several minutes.  So the user can't do much else.  It feels like it's locked up, but have patience.
5. dd_rescue says you can stop it at any time and restart it using the -s option to pick up where it left off (you have to record the last ipos reported by dd_rescue).  I didn't try this.  I just let it run overnight.

---

