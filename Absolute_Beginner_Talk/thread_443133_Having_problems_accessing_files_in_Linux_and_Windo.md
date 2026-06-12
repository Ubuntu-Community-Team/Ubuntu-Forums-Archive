---
title: "Having problems accessing files in Linux and Windows XP"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Prof-KOS on 2007-05-14
I've taken the first leap into Linux by installing the newest version of Ubuntu.  The install went seamlessly and I've installed other software.  I have three partitions on my machine.  

The first is a 40GB drive for my Windows XP Pro installation.
The second is a 140GB partition of a 200GB drive for files.
The Linux partition is the remaining 60GB of the 200GB drive.

While in Linux I was able to access all the files in my second partition and use them with whatever software I needed.  However, when I booted my Windows installation to use a program I haven't found the Linux equivalent of yet, Windows told that the drive had not been formatted and asked if I should format it now.  I would really like to know if this is a normal problem, or if I just missed some setting somewhere to allow me to access the same files in either installation.

Please help me.  I have 100GB of music, movies and other media that I don't want to have to replace.

---

### Post by aeiah on 2007-05-14
what filesystem is your shared 140gb partition using? it should be in FAT32 or NTFS for windows to read it (and FAT32 for linux to read/write by default, although ntfs is possible).

there's a possibility if windows sees but wants to format that there is an error somewhere in it. how many files are there? is it possible to back them up to your linux partition whilst you fiddle around? id suggest booting the gparted live cd and trying to fix the troublesome partition (its an option somewhere) but its good to have it backed up.

---

### Post by Prof-KOS on 2007-05-14
Thanks,  I'll try that.  I actually couldn't use the Live CD installation.  I had to use the non-graphical install.  I believe it was due to my chipset.  I'll try to archive them and back -up the really important stuff and play around.  As long as it should be able to read, I'll figure something out.  

Maybe re-format the partition (after backing up) as a Fat32 partition instead, since it doesn't have any Windows program files on it.

---

### Post by srt4play on 2007-05-14
You didn't answer his question.  What filesystem is on it now? If it's ext3, just install the ext3 drivers for windows and you're all set.

[www.fs-driver.org](www.fs-driver.org)

---

### Post by Prof-KOS on 2007-05-14
The file system is NTFS.  It was partitioned when I first install Windows XP.  What confused me was that I had no problems until I accessed the partition from within Linux.  After that when I booted into Windows the patrition (and all my files) became inaccessible with the error I states earlier.

---

### Post by srt4play on 2007-05-15
You'll make life easier if you backup everything on that partition and reformat it ext3, and then use the drivers I mentioned earlier to access it in Windows.  It's a much more seamless solution than configuring Ubuntu to access NTFS.

But if you want to keep it NTFS, install "ntfsprogs" in synaptic and run this with the partition unmounted:

```
sudo ntfsfix /dev/sda2
```

From your description in your first post it seems like the partition in question is probably /dev/sda2 but change it if necessary. 

After running ntfsfix on it, boot into Windows and try accessing it again.

---

### Post by Prof-KOS on 2007-05-16
Thanks for the advice.  I installed ntfsprogs last night.  However, I'm unsure as to how to find the exactly what the drives Linux designation is (sda2 or another).  I'm obviously very new at this.

I'm pretty sure that at this point the problem is in Windows and not Linux.  I ran the Windows setup disc to see the partitions and the partition's file system was labeled as unknown instead of NTFS.  I'm going to keep trying to find a solution either in Windows or Linux if ntfsfix doesn't work.  There may be a way to tell Windows that the partition is NTFS even if it can't figure it out on its own.  If all else fails I'll take your advice and do a backup onto an external drive and format as ext3.

---

### Post by rich.bradshaw on 2007-05-16
just go to media in the file browser and see what it's called.

sda1 is the first partition on the first drive, sda2 is second on first drive, sdb1 would be first parition on second drive etc.

---

### Post by Prof-KOS on 2007-05-16
Thanks, I'll try this out the evening.  God, I hate feeling like a noob.

---

### Post by Prof-KOS on 2007-05-18
Well, thanks to everyone who offered advice to solve my issue.  It seems that the issue is with the hardware, not any software.  I now can't access the drive at all.  Not even GRUB can load as the partition doesn't even register.  I've reinstalled Linux a native drive.  I'm going to try replacing my IDE cables with a spare I have, just in case it's that simple, otherwise I'll probably have to replace the drive altogether.

---

