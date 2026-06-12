---
title: "Hard drives in Linux: physical and logical"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Palu on 2008-04-20
**Important Edit: By NFS below, I meant ext3. I knew what NTFS was. Not sure how I confused ext3 with the letters NFS. Thanks!**

I have had trouble figuring out exactly how hard drives are treated. I come from a Windows-heavy background. [This thread]("http://ubuntuforums.org/showthread.php?t=640141") explains how to look at a summary of the partitions using fdisk (and with details using some parameters) and at physical drives using df (haven't tried it yet).

Knowing how to look at what I have helps, but I still have questions:
[LIST]
[*]Can a partition span multiple physical drives? Is that a bad idea?
[*]Is NFS the Linux default for file systems? I think I have this part understood: NFS Windows ignores. NTFS Linux can see but not write to. FAT32 both can see and write to but if one has a partition of that, it should be limited to the minimum swap size you can stand because it's slow, bulky, and old. FAT16 is... not worth talking about.
[*]Is NFS resizeable?
[*]Can I resize a partition to include all of a new drive besides what it already includes on the current drive?
[*]How is removeable storage treated? Does it look like it's own partition when you open a file viewer app (or type fdisk -l in bash)?
[*]Can a server I run on my network (it will be Ubuntu too) have a folder shared with my computer so that my computer treats it like a traditional fileshare / local data rather than an ftp-level of functionality?
[/LIST]

**Important Edit: By NFS above, I meant ext3. I knew what NTFS was. Not sure how I confused ext3 with the letters NFS. Thanks!**

---

### Post by LaRoza on 2008-04-20
> **Palu said:**
> 
Knowing how to look at what I have helps, but I still have questions:
[LIST]
[*]Can a partition span multiple physical drives? Is that a bad idea?
[*]Is NFS the Linux default for file systems? I think I have this part understood: NFS Windows ignores. NTFS Linux can see but not write to. FAT32 both can see and write to but if one has a partition of that, it should be limited to the minimum swap size you can stand because it's slow, bulky, and old. FAT16 is... not worth talking about.
[*]Is NFS resizeable?
[*]Can I resize a partition to include all of a new drive besides what it already includes on the current drive?
[*]How is removeable storage treated? Does it look like it's own partition when you open a file viewer app (or type fdisk -l in bash)?
[*]Can a server I run on my network (it will be Ubuntu too) have a folder shared with my computer so that my computer treats it like a traditional fileshare / local data rather than an ftp-level of functionality?
[/LIST]

* Not normally
* No, Ubuntu uses ext3 as default. NTFS can be read and written to by Ubuntu by default. 
* Don't know, probably. Look it up
* If it is contigious, yes
* It looks like a directory mounted under /media. Plug a flash drive in (if it has a label) it will be mounted under /media/<label>. This is the same for external drives, cameras, cds, dvds, and other media. It will show up in Nautilus in the side panel.

---

### Post by sandysandy on 2008-04-20
here are a few links

[http://www.pcguide.com/ref/hdd/file/structPartitions-c.html](http://www.pcguide.com/ref/hdd/file/structPartitions-c.html)

[http://en.wikipedia.org/wiki/Partition_(computing](http://en.wikipedia.org/wiki/Partition_(computing))

regards

---

### Post by Palu on 2008-04-20
**Important Edit: By NFS, I meant ext3. I knew what NTFS was. Not sure how I confused ext3 with the letters NFS. Thanks!**

Ok, so my edit in mind, I meant ext3. That means my resizing question stands still. Now that I call it the right thing, I have found it in Google, haha... so I know I can, but I haven't identified all the ramifications. Does it damage data on a partition if it's, for example, 40% full and I resize it to 50% the old size? Is that safe. Is growing a partition safe? Or should I leave unpartitioned space on my drive in case I need to add to partitions? Or is that only possible with the last partition (and related to your comment about being contiguous?)? Or I will try to begin less sentences with "or" in the future... Thanks for all the info.

---

### Post by hyper_ch on 2008-04-20
nfs is networking file system... so it would be sort of like samba in a windows environement

it's more a protocol on how to mount networked partitions/systems

---

### Post by Palu on 2008-04-20
> **hyper_ch said:**
> nfs is networking file system... so it would be sort of like samba in a windows environement

it's more a protocol on how to mount networked partitions/systems

Then I will be very very interested in that later... once I can run my desktop. :popcorn:

---

### Post by prshah on 2008-04-20
> **Palu said:**
> 
[*]Can a partition span multiple physical drives? Is that a bad idea?

No, it can't. Which means that whether it's a bad idea or not is academic.

> [*]Is ext3 the Linux default for file systems? I think I have this part understood: ext3 Windows ignores. NTFS Linux can see but not write to. FAT32 both can see and write to but if one has a partition of that, it should be limited to the minimum swap size you can stand because it's slow, bulky, and old. FAT16 is... not worth talking about.

Your information is a little dated: ext3 can be seen and written to using EXT2/3 IFS drivers from [www.fs-drivers.org](www.fs-drivers.org). However, permissions issues are ignored, so it's not a good idea to make them write-accessible in Windows.

Linux can smoothly read/write to NTFS partitions, out-of-the-box from Gutsy (Ver 7.10) onwards.

XP seems to have intentionally limited the _creation_ size of a FAT32 partition to 32Gb. If you use some other program to create the FAT32 partition (such as gparted, PartitionMagic, etc), you can cross the 32Gb limit and XP will happily use it, transparently, no funky drivers etc.

> [*]Is ext3 resizeable?
[*]Can I resize a partition to include all of a new drive besides what it already includes on the current drive?

Completely resizeable. And resizing will not (under usual circumstances, 99% of the time) result in the deletion or loss of any data. Note that it _is_ a sensitive operation, and if something goes wrong (power outage, gremlins) you can lose your entire partition, possibly even all your partitions, so better to keep a backup, just in case, before you start mucking about with partitions. Have given that disclaimer; I have done lots of resizing of NTFS, ext3 and FAT32 partitions, without backup, without data loss, with 100% confidence.

However you cannot "merge" two partitions, if that what you mean by include data of new partition in existing partition.

> [*]How is removeable storage treated? Does it look like it's own partition when you open a file viewer app (or type fdisk -l in bash)?

Removable mass storage drivers are treated as any other hard drive, eg; if your device is mounted at /dev/sdd, the first partition will be /dev/sdd1, then /dev/sdd2 and so on. It will be mounted into a similar location at /media/

> [*]Can a server I run on my network (it will be Ubuntu too) have a folder shared with my computer so that my computer treats it like a traditional fileshare / local data rather than an ftp-level of functionality?


Yes, totally transparently. _THAT_ is NFS. :)

> 
 Does it damage data on a partition if it's, for example, 40% full and I resize it to 50% the old size? 

resizing your partition with gparted will not cause any damage to data in any (usual) circumstances. But REDUCING the size of the partition may be difficult in ext3, since files are scattered throughout the partition to prevent fragmentation issues.

> Is growing a partition safe? Or should I leave unpartitioned space on my drive in case I need to add to partitions? 

Perfectly safe; even NTFS. No need to leave unpartitioned space. And talking about partitions, you can have only 4 partitions on a single drive. For more than four, one of them has to be an EXTENDED partition, _within_ which you can create multiple "logical" drives, or "logical partitions" though that term is not essentially correct.

> Or is that only possible with the last partition (and related to your comment about being contiguous?)? Or I will try to begin less sentences with "or" in the future... Thanks for all the info.

You can move your partitions about to consolidate free space, again using gparted, again with the same caveats about power, gremlins, bad sectors, etc.

A final note: Some posters have reported that gparted takes a lot of time, upto and over 12 hours in some cases. On a personal level, I have never faced such a problem: 01:15 hours was the max runtime to resize an NTFS partion from 30Gb to 10Gb, then move and expand an ext3 partition from 10Gb to 60Gb.

---

### Post by Palu on 2008-04-20
Wow... THANKS! :KS

One more thing: I guess I'm still confused on NFS (which I already knew wasn't NTFS) is a Linux concept, I guess, and related to networking... but is it a file system or a service? (Is service = daemon? It seems like I recall them being synonymous but one being more common terminology in Windows and the other in Linux.)

---

### Post by PeterJS on 2008-04-20
> **Palu said:**
> Wow... THANKS! :KS

One more thing: I guess I'm still confused on NFS (which I already knew wasn't NTFS) is a Linux concept, I guess, and related to networking... but is it a file system or a service?

Depends where you look at it from, NFS is both the name of the protocol and the filesystem name. On the serving machine NFS is just the protocol that it uses to communicate with the client machine. On the client machine NFS is both the filesystem type for the remote file system (because of this the client doesn't have to care what the file system really is, ext2/3, reiserfs, xfs, zfs, etc) and the protocol that it uses to communicate with the server.

> 
 (Is service = daemon? It seems like I recall them being synonymous but one being more common terminology in Windows and the other in Linux.)

The two concepts  are tightly bound, daemons provide services. The equivalent windows terminology would be Services provide services.

---

