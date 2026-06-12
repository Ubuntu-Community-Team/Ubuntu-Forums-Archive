---
title: "Computer shut off while resizing my Windows partition"
date: 2013-07-15
forum: Apple Hardware Users
---

### Post by theorange9 on 2013-07-15
So, I was resizing my windows partition using gparted, like I often do, however, I stupidly decided to do it without plugging in my power supply for my macbook, and the computer ran out of battery while the resizing process was happening. Now, gparted states that dev/sda4, my windows partition, has an unknown filesystem, and my windows partition also doesn't show up in Mac OS X finder or the option-key menu at boot anymore, which leads me to believe that either the file system information or the boot information was lost when my computer shut down. Also, I was resizing my windows partition from 115 to 135gb, and gparted states that dev/sda4 is 135gb, so my computer probably shut off after the size-increasy part. I have two ideas of how to fix it at the moment. I have a Windows 8 installation disk that I can use as a repair disk, and I was also going to try using ntfsprogs in a Ubuntu live CD to see if that fixes it. However, since I'm too scared of losing my data before I accidentally overwrite anything, I decided to try and back up my important files, so I dried to mount it in Ubuntu. Strangely enough, when I ran fdisk in ubuntu, it stated that dev/sda4 was actually fat32 system instead of ntfs, and I have no idea why. I tried to mount dev/sda4 as both a fat32 system and a ntfs system, however, in both cases, terminal stated that dev/sda4 did not exist, even though it showed up in fdisk.

Anyone else accidentally shut off their system during partion resizing? There's probably different levels of severity based on where the process was, but I hope none of my personal files were deleted. I really don't mind if I have to erase my partition and reinstall Windows, (although I'd rather not) but I do want to find some way to mount the drive to back up my important files?

---

### Post by lukeiamyourfather on 2013-07-15
If the data is important to you stop everything and take it to a recovery specialist. If you don't really care about the data, probably try the Windows repair utility. Hindsight is 20/20, but that's why they say backup everything before resizing the partition (it comes up in a huge warning box).

---

### Post by theorange9 on 2013-07-15
Perhaps I could clone or image the drive in case I screw something up?

---

### Post by lukeiamyourfather on 2013-07-15
Most cloning software will clone functional partitions, not raw binary data. You could "clone" it to another disk if you have another of the exact model laying around (dd if=/dev/xxx of=/dev/yyy). There's no saying it would actually work, but it might be worth a shot. Again, if the data is important to you then stop what you're doing and take it to a data recovery specialist. The odds are against you being able to recover the data on your own.

---

### Post by theorange9 on 2013-07-15
I am planning on upgrading my 500gb hd to a 1tb hd, maybe I could clone the data onto that?

Is there anyway to just mount dev/sda4, copy some files, then do a complete reinstall?

---

### Post by oldfred on 2013-07-15
Since you were enlarging it, it should not have taken any time and worked. Were you doing other tasks also?

I might try testdisk? It may show the files.
Windows NTFS partitions have to have the same size info in the PBR - partition boot sector as the partition table. You have to run chkdsk to fix that, but with the errors it may just move many files to its chkdsk repair folder.

---

### Post by theorange9 on 2013-07-15
No I was not doing anything else.

I can't run chkdsk at all-I can't even boot into my windows partition. It's not recognized.

I have tried PhotoRec. I guess I'll try TestDisk now.

Also, what do you mean it should not have taken any time?

By the way, in photorec and test disk, there are two entries for each drive- something along the names of *disk0* and *rdisk0, *and they are exactly the same. I read something about rdisk being the raw data of the disk, I have to admit I have no idea what that means.

---

### Post by oldfred on 2013-07-15
Generally moving partitions can take a very long time as it has to copy data, but just increasing the size should just be a write of the new size into the partition table. Or was the space not unallocated that you increased it into?

---

### Post by theorange9 on 2013-07-15
Yeah I grew it into unallocated space. So I'm guessing that because I can't boot from it, there's probably a loss of data, which means that it was still moving?

---

### Post by oldfred on 2013-07-15
It then should not have been moving any data. Unless you had a bad sector of something it should have been very quick. I have done that as a single command in gparted & it just comes right back. Unless you shutdown in the middle which like any power failure or abnormal shutdown can many times cause file corruption.

---

### Post by theorange9 on 2013-07-16
Well, yes, It always moves to the left because the unallocated space is to the left of it.

---

### Post by oldfred on 2013-07-16
Ok a move left is always a very long process as that does have to copy data. And any failure at that point will totally corrupt data as some data may be in one place and some in another.
I do not like to move partitions left because of that, but it does require good backups because of the risk.

---

### Post by theorange9 on 2013-07-16
The reason it actually took time is because the unallocated space is always to the left of /dev/sda4, so when I grow it it also moves to the left.

---

### Post by theorange9 on 2013-07-16
> **theorange9 said:**
> The reason it actually took time is because the unallocated space is always to the left of /dev/sda4, so when I grow it it also moves to the left.

Ignore that, accidentally posted it twice. Sorry.

So, my data is pretty much screwed, or is it still somewhere on the drive, able to be retrieved?

---

### Post by oldfred on 2013-07-16
Not exactly sure how it copies. What ever was in the middle as it was copying is gone, but you may be able to recover some or most of your data. I have used photorec. It is a long slow process, and requires a lot of work after the fact as it cannot recover file names. It just scans hard drive for anything that looks like a file. You need another drive with lots of room for recovered data. For me I was recovering text files that I regularly save. My backups were old and photorec found my text files. It just also found all the deleted copies and I never was sure I found the most current. A lot of manual file compares.

Photorec is part of testdisk which I would try first. If it sees files then you can copy with file names.
       Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

   Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

### Post by theorange9 on 2013-07-16
What exactly is the difference between photorec and testdisk? Also, when selecting which drive to scan, should I be selecting the raw data or the normal drive? Not exactly sure what the difference is.

---

### Post by oldfred on 2013-07-16
I have not seen the raw data version of testdisk. I just have used it where it only showed system.
Testdisk will try to restore partitions and full partition information. Best if it works.
Photorec only scans drive for files and without partition info there are no file names, just the extension or file type.

---

### Post by theorange9 on 2013-07-17
How risky exactly is this? I'm probably just going to buy a new hard drive and maybe back up my stuff to that. Should I back up before I run TestDisk?

---

### Post by oldfred on 2013-07-17
Once data is gone, it may be more risky to try to recover it. Some suggest a full dd image copy to a file and just work on the image. But if data was that valuable were you not backing it up?

Some info here on imaging a drive.
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

      
 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

---

### Post by theorange9 on 2013-08-12
Hello again, sorry I haven't replied in a while, I've been sort of procrastinating it for a while, and I just got a new hard drive shipped to me.

So, how would I go about cloning my old drive onto my new drive? At first, I tried using a program on mac called [Carbon Copy Cloner](http://www.bombich.com), but then I realized that a partition has to be mounted for it to be cloned.

Should I just use something like Clonezilla? Is Clonezilla able to clone a drive bit by bit, so that even all the corrupted files are cloned?

---

### Post by oldfred on 2013-08-12
You can use gddrescue. Info in link posted before. I have never used it. Do not leave drive plugged in after cloning as the duplicate UUIDs may confuse system. You cannot have both drives plugges in after you copy without changing UUIDs, but you probably will be reformatting one or the other drive anyway.

---

### Post by theorange9 on 2013-08-13
Hi oldfred, thank you for all the help that you have given me.
I tried to used testdisk to fix my problem, however, I encountered some problems with it, so I started a new thread [here](http://ubuntuforums.org/showthread.php?t=2167241&p=12755063).

If testdisk ends up not working, I may try ddrescue.

---

