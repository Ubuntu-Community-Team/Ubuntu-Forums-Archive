---
title: "Advice on partitioning and formats for dual-boot"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by trishacupra on 2007-04-18
Hi,

Apologies in advance for my clumsy wording. I'm not very familiar with this terminology yet, so please ask for clarification where necessary.

I'm going to install Feisty when it's released in a few days, and dual boot it with Windows XP Home (hopefully until I  get rid of Windows forever, one day).

I'm currently running WinXP on my laptop, which has a 40GB physical hard drive split into two partitions - a 10GB recovery partition, and 30GB with Windows and programs installed. Right now I have a 30GB external hard drive (30GB) in FAT32 format with my data on it. Actually, I just copied everything on it onto my iPod and my internal drive, because I'm about to take the external hard drive out of the enclosure and put a 400GB hard drive into that enclosure instead, and then copy all those data files onto that one.

It just occurred to me that I'll have to format that hard drive, and I'm trying to decide what format (or is the term 'file system?') to use. At first I thought I was just going to use FAT32, but then I read some things about the limitations of FAT32, like a 4GB file size limit, and some stuff that makes me wonder if I can actually format a 400GB hard drive in FAT32 - or is 400GB too big?

And then I remembered this article: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) and that there is another format - Ext3. And that article mentions accessing the files on the drive via Windows using this software: [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html). Apparently it doesn't have the limitations that FAT32 has.

Since I plan to use Ubuntu about 80% or more of the time (I'm serious about weaning myself off Windows), I figure that if Ext3 is a superior file system and that software makes Windows able to access my files, then that would be best for the external hard drive.

I plan on using my laptop's internal hard drive for my recovery partition that's already there, and split the other partition into a Windows XP OS partition (NTFS), a Ubuntu OS partition (Ext3), and a little swap thingo partition. All my data would be on external hard drive/s. (My Dad taught me to keep the OS and data files separate, in case the OS goes up in smoke.)

So, with all that in mind, should I make my 400GB external hard drive FAT32 or Ext3, considering only data files will be on it, and I need to write to it mostly with Ubuntu, and occasionally with WinXP?

By the way, I considered installing Ubuntu on the external hard drive, but because it's a laptop, I don't want to have to take the external hard drive everywhere just to watch a DVD or whatever on the laptop. It would make it a little less portable.

Thanks for any suggestions/experiences you have.

---

### Post by mikewhatever on 2007-04-18
The 4 GB limitation in FAT32 applies to file size, not partition, so it is really up to you how to format it. EXT3 is a more efficient file system, but if the drive is used for storage, you might not notice any difference.

---

### Post by trishacupra on 2007-04-18
So, is the stuff I read about Windows only being able to see 32GB of a larger FAT32 drive outdated?

---

### Post by heimo on 2007-04-18
Seems like a good plan to me. I haven't used EXT2 IFS, so I can't comment on it, but it looks like what you could use. Check the FAQ and release notes.
[http://www.fs-driver.org/faq.html#acc_ext3](http://www.fs-driver.org/faq.html#acc_ext3)
[http://www.fs-driver.org/relnotes.html](http://www.fs-driver.org/relnotes.html)

---

### Post by heimo on 2007-04-18
> **trishacupra said:**
> So, is the stuff I read about Windows only being able to see 32GB of a larger FAT32 drive outdated?

During setup in XP and 2000:
[http://en.wikipedia.org/wiki/Fat32#FAT32](http://en.wikipedia.org/wiki/Fat32#FAT32)

---

### Post by trishacupra on 2007-04-18
> You cannot format a volume larger than 32 gigabytes (GB) in size using the FAT32 file system during the Windows XP installation process. Windows XP can mount and support FAT32 volumes larger than 32 GB (subject to the other limits), but you cannot create a FAT32 volume larger than 32 GB by using the Format tool during Setup. If you need to format a volume that is larger than 32 GB, use the NTFS file system to format it. Another option is to start from a Microsoft Windows 98 or Microsoft Windows Millennium Edition (Me) Startup disk and use the Format tool included on the disk.

Source: [http://support.microsoft.com/kb/314463](http://support.microsoft.com/kb/314463)

Does that apply to external hard drives, or just the primary one? 

By the way, if I want to make the external hard drive Ext3, I have to do that using Ubuntu, don't I? Can someone please point me to an article/tutorial on how to format an external hard drive using Ubuntu, please?

---

### Post by mikewhatever on 2007-04-18
> **trishacupra said:**
> So, is the stuff I read about Windows only being able to see 32GB of a larger FAT32 drive outdated?

Yes, I think a FAT32 partition is limited to 32 GB size, but that seems to be a MS made limitation.

---

### Post by rillip on 2007-04-18
My honest suggestion would be to break it into multiple, different partitions with different file systems.  Fat 32 Just Works(tm).  Linux likes it.  Windows likes it.  They play well together.

NTFS has Linux support now.  Some people have good luck with it.  I personally struck out with it.  I'm not willing to invest the time to get it to work when Fat 32 is usable for me and Just Works.

Ext3 is superior to Fat 32, and has Windows support now.  Again, results vary.

It depends entirely on how much you're interested in making this work.  If you just want to go, and you're not concerned all that much about the very picky things about granularity, striping, block size, etc., you just want to have files, use Fat 32 (unless you have > 4gig files).  The nice thing about ext3 is it doesn't really fragment.  If you're willing to play with 'Doze working with it, go for it.  

If I were in your position, I'd make a LARGE fat 32, a medium ext3, and a small ntfs.  Try and get the ext3 working. If it doesn't work out for you, you can abosrb it into the others. Then I'd try and get the ntfs working. If not, same thing.  Worse case scenario, you've got it mostly set up for Fat32, which WILL work.

Edit: Just reread after seeing the other replies.  Large is relative, I'm used to working with MUCH smaller disks.  Maybe try making two Fat32 paritions, one < 32 gig, one > 32 gig, see if the big one works.  Good experimenting! ;)

---

