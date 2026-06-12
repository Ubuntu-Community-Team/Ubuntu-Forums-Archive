---
title: "NTFS vs FAT32"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by stef_204 on 2006-08-28
i will be trying ubuntu desktop cd version.
i have ample unallocated space on my external firewire drive and plan to either create a primary (or extended) partition there for use with ubuntu.
question 1: it wd be nice of course to be able to share with Win XP whatever docs i might create with openoffice (for example).
thus, i am thinking of formating the new partition as FAT32.
however, i am led to believe there are 3rd party aps that can help ubuntu read and write to NTFS.
safety is a concern to me; not corrupting a/g etc. so am i better off forgetting about NTFS totally?
also, i cd format partition linux format only (what is it called again?) but then wd have to boot into ubuntu each time wanted to access data; which may be a nuisance.
question 2: i will also be creating a 20 GB partition for swap files, etc. in same drive but linux format only.  does it make any difference is partition that contains swap, etc. is primary or extended?
recommendations? tx!

---

### Post by mssever on 2006-08-28
[LIST=1]
[*]I would definitely recommend using FAT32 over NTFS. However, you should consider using ext3, as it doesn't get fragmented as bad and it also preserves Linux permissions (FAT has no permissions). You can download a free Windows driver from [http://www.fs-driver.org/](http://www.fs-driver.org/) that will let Windows safely use ext2/3.
[*]It doesn't matter where the swap partition is located, although you might get better performance if it's in the middle of the disk. But you can't just store files on swap. Swap functions as additional RAM. And you probably only need 1GB of swap at the very most.[/LIST]

---

### Post by Paul133 on 2006-08-28
Not really related but...I have a 1GB flash drive. I'm wondering if I can tranfer files from Linux to Windows and vice versa via the flash drive. It's supposed to work with Linux 2.4.x I think it'll work, but I just want to be sure.

---

### Post by mssever on 2006-08-28
> **Paul133 said:**
> Not really related but...I have a 1GB flash drive. I'm wondering if I can tranfer files from Linux to Windows and vice versa via the flash drive. It's supposed to work with Linux 2.4.x I think it'll work, but I just want to be sure.

You shouldn't have any problems with a flash drive...assuming it's FAT32 or its ext2/3 and you have the Windows ext2 driver.

---

### Post by Toxicity999 on 2006-08-28
To the O.P. There ARE program sets geared to have ntfs write support but quite simply it's not easy and doesn't have a great success rate... now you can get away with using fat32 which will be way more kind to ubuntu but within your windows environment you might find restrictions like compression and such... now if space isn't an issue by all means go with fat32 for the windows install. The best thing to do if you have the space and want the 'features' of NTFS is to create a fat32 'pass along' which you mount in both OSes to share some data... if you want to get really into it you could manage to backup all your mail and such there. This 'Pass along' can also be ext3 believe it or not as there are free tools for windows to mount ext partitions... to put it simply:

1)Use Fat32 if you Don't need what NTFS provides for your Windoze install.
2)Use NTFS but have a 'pass along' partition for sharing data easily formatted as either Fat32 or Ext3, both OSes will easily read Fat32 though, keep that in mind.

So either way there's some small loss of function... but you can accomplish what you're looking for easily enough.

---

### Post by mssever on 2006-08-28
> **Toxicity999 said:**
> So either way there's some small loss of function... but you can accomplish what you're looking for easily enough.

If you use ext3 with the Windows driver, there's no loss of function...

---

### Post by stef_204 on 2006-08-29
i'll check the driver out and see about ext3; if windows can read that, then it's fine.
what about size of partition for root, swap, and whatever else native to linux? how much space sd i allocate to those?
can these all be in an extended partition formatted ext.3 but each in its own logical drive?  or do i need to make separate partitions for each of swap, root,. etc.?
tx again!

---

### Post by mssever on 2006-08-29
> **stef_204 said:**
> i'll check the driver out and see about ext3; if windows can read that, then it's fine.
what about size of partition for root, swap, and whatever else native to linux? how much space sd i allocate to those?
can these all be in an extended partition formatted ext.3 but each in its own logical drive?  or do i need to make separate partitions for each of swap, root,. etc.?
tx again!

Deciding on a partitioning scheme is perhaps the most difficult part of installing Linux. First, the easy part. Linux doesn't care whether you use regular or logical partitions. Do whatever best suits your situation.

The next easiest part is swap. The old rule of thumb was that it should be twice your RAM. But if you have at least 512 MB of RAM, than 512 MB of swap should be sufficient. If you want to play it safe, you can go higher, or if you'll be doing memory-intensive work, you might add more. On my laptop, I have 512 MB RAM and 512 MB swap. This was the instaler's default. I occasionally feel like I could use more memory, but I'd rather do that by adding more RAM. On my desktop, I have 256 MB RAM and 3GB swap (historical reasons), and it's really excessive. I'd say don't go over 1 GB unless you're going to be doing some serious memory-intensive work.

As for the rest, Ubuntu will run on as little as 2 GB, but you'll be quite limited in what you can do. I would recommend 10 GB for a reasonably spartan system. But if you have the space, I'd go bigger. On my laptop, I wish I'd squeezed Windows much more than I did, as I find myself hardly using Windows anymore, and I have an NTFS partition taking up more than half my disk while being only 50% full. Here's one website about planning partitions: [http://psychocats.net/ubuntu/partitioning.html](http://psychocats.net/ubuntu/partitioning.html). And remember, If you use the Windows ext driver, than you don't need the FAT32 partition for dual booting.

You should decide if you want one big Linux partition (/) or if you want multiple Linux partitions (e.g., / and /home). The advantage of one big partition is that you don't need to know anything about which parts of your system will use the most space. The advantage of having separate partitions is that they can make your system more managable, especially if you have a separate /home partition. In this case, if you ever decide to reinstall--or even to install/switch to another distribution--your personal files won't be affected. You blow away / where the system files are, and all your stuff lives on /home, which you would leave intact.

One other thing you might consider is leaving some of your disk unpartitioned. The reason for this is that you'll likely have a better idea of where you need disk space down the road a bit. And if you have unpartitioned space, than it's trivial to make a new partition. And with Linux, you can insert that partition transparently into the filesystem in whichever directory you need space. To illustrate how this works, I'll list the partitions on my desktop (spread across two internal hard drives and one external USB drive). This is probably more complex than you need, but it illustrates the power of multiple partitions. Each directory is where it appears (and it's transparent, so it looks like just another folder):
```
[FONT=Courier New]/                  ext3 
/boot              ext3
/home              ext3
/home/mp3          ext3
/home/scott/bin    ext3
/media/hda2        ext3
/media/EXTERNAL_HD vfat
/win/c             vfat
/win/d             vfat[/FONT]
```

---

