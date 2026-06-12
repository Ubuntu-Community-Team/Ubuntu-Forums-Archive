---
title: "[SOLVED] Optimal partition configuration for backup HD of a dual boot computer"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-09-13
I have two computers: one is dual boot Win98/Feisty, and the other is XP/Feisty. I am setting up backup hard drives for each (completely separate hard drives, one for each computer).

My question is, what is the optimal partition configuration for each of these hard drives. For example, should I just leave each HD as 1 FAT32 partition, or should I set up two partitions on each HD-- for example FAT32/EXT3 for the Win98/Feisty computer, and NTFS/EXT3 for the XP/Feisty computer? 

Is there any benefit to having a separate partition for Windows files in FAT32 (or NTFS)  and Linux in ext3? Any benefit at all?

Or on the other side, is there any benefit to having the whole backup disc as one fat32 partition for both Windows and Linux backup?

If you were going to set up a backup HD, how would you do it?

Would you recommend one partition or two. And if one partition, then which should it be: NTFS, FAT32, or ext3? And if two partitions, then what should they be?

---

### Post by logos34 on 2007-09-13
For XP/Feisty I'd make the backup disk either all NTFS or all ext3.  If the former, get [ntfs-3g]("http://www.ntfs-3g.org/index.html") so linux can write to it; if the latter get [fs-driver]("http://www.fs-driver.org/faq.html") so windows can read+write to ext3.  (personally I'd go with ext3 simply because it's a better fs).  For win98/Feisty I think it would be wise to make it half and half: fs-driver won't work on win98, and if you have any linux files 4 GB or larger (for instance large DVD isos or video files, or partition image backups) they can't be stored on fat32 (4 gb file size limit), so will have to go on ext3.

---

### Post by startherepodcast on 2007-09-13
Well, if youe got enogh time, eg. at night you can I think use dd to copy the whole drive to the other so u can boot it directly and keep on working like u did before. I never did this but I think dd copies everything, even the MBR and the partition tables...

---

### Post by swarup on 2007-09-14
> **logos34 said:**
> For XP/Feisty I'd make the backup disk either all NTFS or all ext3.  If the former, get [ntfs-3g]("http://www.ntfs-3g.org/index.html") so linux can write to it; if the latter get [fs-driver]("http://www.fs-driver.org/faq.html") so windows can read+write to ext3.  (personally I'd go with ext3 simply because it's a better fs).  For win98/Feisty I think it would be wise to make it half and half: fs-driver won't work on win98, and if you have any linux files 4 GB or larger (for instance large DVD isos or video files, or partition image backups) they can't be stored on fat32 (4 gb file size limit), so will have to go on ext3.

I see. That is very interesting and educative. 

In view of what you've explained, I think for us (since we really don't keep large files on these computers), it may even make most sense to go with a single fat32 partition. One single-partition fat32 backup HD, a separate one for each computer. It seems like the whole rational for wanting two partitions is for the possibility of needing to backup files of greater than 4GB size, which fat32 can't handle. 

If one doesn't have the need for backing up large files like that, then in that case it seems like the backup process is simpler with one partition. One fat32 partition. Otherwise one needs a backup utility that can backup files from both native partitions, to both backup partitions. It involves two totally setup backups, to different backup destinations. --Unless one's backup utility can handle such a complex backup command with two different destinations depending on which partition the file comes from. Can sbackup do this? Or if not, is there a (preferably free) backup utility that can?

(I don't need to make a full mirror backup of my hard drives as the other fellow suggested-- rather, just specific personal data files--but thank you anyway.)

---

### Post by logos34 on 2007-09-14
> **swarup said:**
> --Unless one's backup utility can handle such a complex backup command with two different destinations depending on which partition the file comes from. Can sbackup do this? Or if not, is there a (preferably free) backup utility that can?

I was just looking through Sbackup's documentation and I don't see anything about multiple backup profiles with different destinations.  I don't think rsync has that option either, not sure though.  Maybe you could use tar, create two different cron job profiles to run at different times with different folders and destination disks.

---

### Post by swarup on 2007-09-14
> **logos34 said:**
> I was just looking through Sbackup's documentation and I don't see anything about multiple backup profiles with different destinations.  I don't think rsync has that option either, not sure though.  Maybe you could use tar, create two different cron job profiles to run at different times with different folders and destination disks.

My question is: this all sounds very complex. What do *most* people do who maintain dual boot computers? There are an awful lot of people out there who use dual boot computers. That means they have two partitions to back up. How do most people do it? There must be some common solution which most folks use.

---

### Post by logos34 on 2007-09-14
Whenever I'm in windows (not often these days) I do an incremental using NTI Backup!  In linux I use either tar or sbackup for my /home dir files (or just cp the main stuff to the backup disk), and dd or partimage to periodically make a gzipped image of the root partition.

---

### Post by swarup on 2007-09-15
I see. Interesting. Does your backup HD have one partition, or two? And what file type is the partition(s)?

What does dd stand for? I found partimage in Synaptic Package Manager, but "dd" does not seem to yield any particular application. Is there a fuller name for this utility?

---

### Post by logos34 on 2007-09-15
[This ]("http://en.wikipedia.org/wiki/Dd_(Unix)")should answer your questions about dd.

It's split  ntfs/ext3.  The only reason it's not all ext3 is I run XP Pro x64 and fs-driver doesn't support that architecture, so I can't access ext3.  

NTI Backup has served me well, but I may start using cp or tar for my windows partitions too, as described [here]("http://www.brunolinux.com/10-General_Info/Backup_Windows_in_Linux.html").

---

### Post by swarup on 2007-09-16
> **logos34 said:**
> [This ]("http://en.wikipedia.org/wiki/Dd_(Unix)")should answer your questions about dd.

Sounds a bit complex, like I'd have to learn a whole new language just to use it.

> **logos34 said:**
> It's split  ntfs/ext3.  The only reason it's not all ext3 is I run XP Pro x64 and fs-driver doesn't support that architecture, so I can't access ext3. 
 
I see. So if one has a dual boot with standard XP/Ubuntu, or Win98/Ubuntu, then there is really no need to maintain a dual partition on the backup drive. One ext3 partition is really all that is needed, for full read/write privileges in both directions.

> **logos34 said:**
> NTI Backup has served me well, but I may start using cp or tar for my windows partitions too, as described [here]("http://www.brunolinux.com/10-General_Info/Backup_Windows_in_Linux.html").

Now that I've understood that one can put all file types from both internal partitions onto a single-partition ext3 backup drive, for me it seems to make sense to just backup all material from both internal partitions using the sbackup utility in Ubuntu, and have a single destination for everything: a  external drive with ext3 file system. Does that sound reasonable?

---

### Post by logos34 on 2007-09-16
> **swarup said:**
> 
I see. So if one has a dual boot with standard XP/Ubuntu, or Win98/Ubuntu, then there is really no need to maintain a dual partition on the backup drive. One ext3 partition is really all that is needed, for full read/write privileges in both directions.

yes, except you can't use fs-driver on win98 in order to access  ext3.  There might be another app though

> Now that I've understood that one can put all file types from both internal partitions onto a single-partition ext3 backup drive, for me it seems to make sense to just backup all material from both internal partitions using the sbackup utility in Ubuntu, and have a single destination for everything: a  external drive with ext3 file system. Does that sound reasonable?

yes, doing the whole shebang from the linux side seems to me the best strategy. There  might even be a way with sbackup to span it over multiple drives if too large for one--not sure but I know you can do it with rsync.

---

### Post by swarup on 2007-09-17
I see. That's all great info.

I don't think I can think of any further questions to ask you about this at this time-- you've answered them all. I'm all questioned out. Thanks for all your help. :)

---

