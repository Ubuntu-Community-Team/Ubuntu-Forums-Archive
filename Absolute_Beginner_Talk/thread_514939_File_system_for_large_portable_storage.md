---
title: "File system for large portable storage?"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by jarviw on 2007-08-01
I read a few other threads, but decided to post anyways...

I am talking about a 500G external HD, that I want to use for backup all my CDs in FLAC (and solely for that purpose).  **What file system should I use for this external 500G HD?**

ext3 -  Do I really need a journaling FS?  Not like I am going to run an OS on this HD anyways... and I find it rather slow!  Also, it will be quite annoying as a portable storage for Windows machines.

NTFS - great for Windows, supported in linux, but what's so good about it??

FAT32 - does it even support 500G?

any suggestions??

---

### Post by asmoore82 on 2007-08-01
ext3 or reiserfs

YOU NEED A JOURNALED FILESYSTEM!!

ext2 and ext3 are blazingly effecient; but a power hiccup on a busy ext2 system WILL b0rk your data.

---

### Post by Ek0nomik on 2007-08-01
FAT32 will allow you do use it on Linux boxes and Windows boxes as soon as you plug it in.  The only drawback of FAT32 is it won't let you have a single file greater than 4GB.  A single song, even in .flac format, shouldn't be 4GB.  :)

The NTFS support in Linux doesn't work out of the box, and even when you do get it to work, it isn't the best choice.

---

### Post by asmoore82 on 2007-08-01
> **Ek0nomik said:**
> FAT32 will allow you do use it on Linux boxes and Windows boxes as soon as you plug it in.  The only drawback of FAT32 is it won't let you have a single file greater than 4GB.  A single song, even in .flac format, shouldn't be 4GB.  :)

The NTFS support in Linux doesn't work out of the box, and even when you do get it to work, it isn't the best choice.

FAT32 can't go over 20GB per filesystem
extended partitioning FTW?!? :lolflag:

---

### Post by Ek0nomik on 2007-08-01
> **asmoore82 said:**
> FAT32 can't go over 20GB per filesystem
extended partitioning FTW?!? :lolflag:

Yes it can.  It can go as high as 2TB as far as I know.  I have a 250GB and a 500GB hard drive as FAT32.

---

### Post by Inxsible on 2007-08-01
I made my external 500 GB a EXT3 drive ( that was the phase, when I loved Ubuntu so much that I wanted to get away from all things Microsoft)

I still have it as EXT3.

The problems I have are
1) I cant connect it to my Windows machines without installing FS- Driver on them. I have installed it on all my windows machines so that works out OK.
2) I cannot connect it to others Windows Machines -- This could be a pro or a con. I dont have to lend out my drive to others(which is a good thing) but sometimes when I need something from them, I have to use an old 1GB flash drive for it or borrow their drive. (I plan to buy a 160 GB protable drive and keep that as FAT - to mitigate this problem)
3) FS-Driver gives problems at times. Nothing that a reboot wont resolve in Windows, however. So its not serious.


So if you are gonna use your hard-drive with only Linux machines most of the time --- Use EXT3
if you are gonna use it only on YOUR machines - you can use EXT3 or NTFS or FAT(if you are sure you will never have file size > 4GB- which I have never seen yet)
if you are going to move around your drive and use it with other people's machines too, your best bet would be--- NTFS or FAT

---

### Post by Steve1961 on 2007-08-01
> **Ek0nomik said:**
> Yes it can.  It can go as high as 2TB as far as I know.  I have a 250GB and a 500GB hard drive as FAT32.

Yep, it is a 2 TB limit.  People often mistake the inability of windows to create a fat32 partition greater than 32gb as a limitation of the filesystem.

---

### Post by asmoore82 on 2007-08-01
> **Ek0nomik said:**
> Yes it can.  It can go as high as 2TB as far as I know.  I have a 250GB and a 500GB hard drive as FAT32.

Ahh it was a Windows 2000 problem ... 
[http://www.microsoft.com/technet/prodtechnol/windows2000serv/reskit/core/fncc_fil_tvjq.mspx?mfr=true](http://www.microsoft.com/technet/prodtechnol/windows2000serv/reskit/core/fncc_fil_tvjq.mspx?mfr=true)

but reiserfs is still faster than ext3 which is incredibly faster than FAT

---

### Post by Inxsible on 2007-08-01
> **Steve1961 said:**
> Yep, it is a 2 TB limit.  People often mistake the inability of windows to create a fat32 partition greater than 32gb as a limitation of the filesystem.

Hmmm.. Its been a long time since I had FAT32 partitions, so I didn't know Windows couldn't create >32 GB partitions on FAT.

Now my question is, If i create a >32 GB partition on FAT with Linux, will the entire drive be accessible thru Windows, or would I have to create 32 GB partitions?
If Windows cannot access more than 32 GB, I will have to format my new 160 GB drive to NTFS :)

---

### Post by Steve1961 on 2007-08-01
> **Inxsible said:**
> Hmmm.. Its been a long time since I had FAT32 partitions, so I didn't know Windows couldn't create >32 GB partitions on FAT.

Now my question is, If i create a >32 GB partition on FAT with Linux, will the entire drive be accessible thru Windows, or would I have to create 32 GB partitions?
If Windows cannot access more than 32 GB, I will have to format my new 160 GB drive to NTFS :)


You should be able to access them without a problem.  I have a 200GB fat32 partition and windows can read and write to it without issue.

---

### Post by fastpakr on 2007-08-01
Why not just use NTFS?  NTFS-3g works great on Linux now, and you know it will work on the Windows side.

---

### Post by dannyboy79 on 2007-08-01
> **asmoore82 said:**
> FAT32 can't go over 20GB per filesystem
extended partitioning FTW?!? :lolflag:

wrong. I have a 200GB fat32 external usb hard drive currently. it was formatted with WinXP Pro

I have both an external drive with ext3 and a external drive with NTFS. both seem to be working without a hitch in each other's system. (Winxp w/ FS-Driver) (Linux w/ NTFS-3G)

---

### Post by Ek0nomik on 2007-08-01
> **fastpakr said:**
> Why not just use NTFS?  NTFS-3g works great on Linux now, and you know it will work on the Windows side.

In my opinion, it's best to work with things that will work right out of the box.  I don't want to use third party support in order for my filesystem which holds a lot of important data to be used properly.

It seems as though NTFS-3G is widely praised on these forums though.  ;)  I used it and decided I would rather switch to something that was implemented to work without extra support.

---

### Post by fastpakr on 2007-08-01
Fair enough - it sounds like FAT32 fits your needs pretty well also.  Definitely use one of those two for Windows portability, since Windows doesn't cleanly work with Linux format partitions.

---

### Post by jarviw on 2007-08-01
Hmmm... I think the size limit of FAT32 in Windows is only during Installation. I was just reading about it over wikipedia.

But yes, most likely I will not need to worry about the file size limit of FAT32... 1 CD, even an 80 min track, will top 700 MB most... half that for FLAC.  But should I worry about file system corruption?  some file corruption once in a blue moon should be tolerable, but losing ripped 400 CDs does translate to a huge amount of time spent ripping them!

I think I will really worry about the whole file system integrity!


ext3, I can see how journaling FS can be advantageous for external drive... but what is with it taking ~10% of total capacity to be used for journaling anyways?  I sweat to god, every time I format a HD from FAT/NTFS to ext3, I lose about 10% of total capacity!  
And again, it is a pain to share an ext3 partition with none linux people!  the extra driver to install, annoying reboots, and the residue driver letter afterward! (it's not supposed to be there, but it happened!)


NTFS, supported but not perfect... always an extra command line to mount-- I can live with that though.  Is the NTFS file system integrity better than FAT32?  I intuitively think so... but I can very much be wrong.

---

### Post by fastpakr on 2007-08-01
> **jarviw said:**
> ext3, I can see how journaling FS can be advantageous for external drive... but what is with it taking ~10% of total capacity to be used for journaling anyways?  I sweat to god, every time I format a HD from FAT/NTFS to ext3, I lose about 10% of total capacity!  

I think [this](http://boncey.org/2006_11_18_reclaiming_ext3_disk_space) will explain (and fix) your issue with disappearing space on ext3 partitions.

---

### Post by Ek0nomik on 2007-08-01
> **fastpakr said:**
> I think [this](http://boncey.org/2006_11_18_reclaiming_ext3_disk_space) will explain (and fix) your issue with disappearing space on ext3 partitions.

From the webpage:

> some poster on some Internet forum says it's probably OK to do away with that reserved space.
*That's usually good enough for me*

:lol: :lol:

I love how true that statement is for near all of us.  :)

---

### Post by qamelian on 2007-08-01
> **Steve1961 said:**
> Yep, it is a 2 TB limit.  People often mistake the inability of windows to create a fat32 partition greater than 32gb as a limitation of the filesystem.

Actually, it's an artificial limit imposed by Microsoft and doesn't affect all versions of Windows. Windows ME was quite happy to partition the 120GB drive I use for audio work into a single 120GB parttition, but XP prevents you from going above 32GB. The same is true of the 4GB limitation on file size. On WinME, I routinely streamed 10GB chunks of video from my DV camera to my hard drive. Imagine my horror when, after upgrading to WinXP I could no longer access those files becasue XP decided they were too big!

---

### Post by wolfen69 on 2007-08-01
i would go ntfs. then it could be hooked up to any machine.

---

### Post by Inxsible on 2007-08-01
> **jarviw said:**
> ..... and the residue driver letter afterward! (it's not supposed to be there, but it happened!)

You can get rid of the--correctly termed--"residue drive letter" by changing the Id of the drive to 7(id for NTFS drives) from 83(id for linux drives). Changing this id does not affect the file system, and this id is read only on connection. 

Only after I changed the id to 7, was I able to get rid of the residue drive letter and was also able to plug-n-play the drive in Windows.

The CATCH: your sudo fdisk will show it as a NTFS drive instead of Linux Drive(i think) -- but I can live with that !

It was quite some time back that I did this, so I dont remember the exact HOWTO, but searching on this forum would be a good bet.

---

### Post by dannyboy79 on 2007-08-01
> **qamelian said:**
> Actually, it's an artificial limit imposed by Microsoft and doesn't affect all versions of Windows. Windows ME was quite happy to partition the 120GB drive I use for audio work into a single 120GB parttition, but XP prevents you from going above 32GB. The same is true of the 4GB limitation on file size. On WinME, I routinely streamed 10GB chunks of video from my DV camera to my hard drive. Imagine my horror when, after upgrading to WinXP I could no longer access those files becasue XP decided they were too big!

again, I am sorry to say that this is not true. I have a FAT32 partition within Linux and I can't save a xbox iso that is larger than 4gb on it.


I did misspeak earlier, my 200gb FAT32 partition was formatted with Gparted within linux NOT WinXP Pro.
(About my earlier statement regarding 32gb partition creation within WinXP Pro.)

Not sure what the person was complaining about when saying that the Filesystem overhead is horrible for ext3, heck, I got a 500gb hard drive, formatted as ext3 and it is 488. When I formatted a 120gb in NTFS I am left with 111. Seems pretty proportional to me. In fact, if you do a proportional equation putting 500 over 488 and 120 over "X", then cross multiply 488 by 120 and then divide the total by 500, if it were the ext3 filesystem, you should be left with 117 ("X" would be 117). With NTFS, I was left with 111 so it's worse overhead in NTFS than with ext3. This was my experience anyway.

If you know that you won't ever need to save anything over 4gb, than go with fat32 for sure. Otherwise I'd go with NTFS, this way you don't have to have you're friends install FS-Driver

---

### Post by dannyboy79 on 2007-08-01
> **Inxsible said:**
> You can get rid of the--correctly termed--"residue drive letter" by changing the Id of the drive to 7(id for NTFS drives) from 83(id for linux drives). Changing this id does not affect the file system, and this id is read only on connection. 

Only after I changed the id to 7, was I able to get rid of the residue drive letter and was also able to plug-n-play the drive in Windows.

The CATCH: your sudo fdisk will show it as a NTFS drive instead of Linux Drive(i think) -- but I can live with that !

It was quite some time back that I did this, so I dont remember the exact HOWTO, but searching on this forum would be a good bet.


this can be done with Testdisk which is on the Gparted Live cd which is a must have for any person.

---

### Post by Ek0nomik on 2007-08-01
> **wolfen69 said:**
> i would go ntfs. then it could be hooked up to any machine.

You can't hook an NTFS drive up to Linux without adding support for it.

NTFS is not the best option if you need to work cross platform!

---

### Post by Inxsible on 2007-08-01
> **Ek0nomik said:**
> You can't hook an NTFS drive up to Linux without adding support for it.

NTFS is not the best option if you need to work cross platform!

True, but you gotta use some software right? ntfs-3g has been pretty stable by most accounts. Just 'cause a software doesn't come pre-bundled with the OS, doesn't mean it ain't good. I am sure you too have software on your machine that didn't come pre-bundled with the Ubuntu OS

Besides, there ain't no harm in being ready for that >4GB file that you might get(altho, currently I don't see it) ;)

---

### Post by dannyboy79 on 2007-08-02
> **Inxsible said:**
> True, but you gotta use some software right? ntfs-3g has been pretty stable by most accounts. Just 'cause a software doesn't come pre-bundled with the OS, doesn't mean it ain't good. I am sure you too have software on your machine that didn't come pre-bundled with the Ubuntu OS

Besides, there ain't no harm in being ready for that >4GB file that you might get(altho, currently I don't see it) ;)


i agree. it all depends on exactly what the disk will be used for, and I gurantee that one day you  need to put a huge file on it, the person will be cussing up a storm. What I did before I became more confident using ntfs-3g was formatted a 200gb harddrive into 2 partitions. majority was FAT32 and 15gb was NTFS just in case.

---

