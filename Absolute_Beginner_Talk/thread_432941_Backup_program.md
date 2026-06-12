---
title: "Backup program?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by mech7 on 2007-05-04
Is there any good backup program for ubuntu.. something simple to make incremental backups of files and such :)

---

### Post by nanotube on 2007-05-04
i use rdiff-backup
it's a commandline tool, though, i don't know if you are looking for something gui-based.

---

### Post by LaRoza on 2007-05-04
```

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

```

This will backup your entire system.

---

### Post by nanotube on 2007-05-04
> **LaRoza said:**
> ```

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

```

This will backup your entire system.

but that doesn't do incremental backups like he wants...

---

### Post by aysiu on 2007-05-04
*rdiff-backup* is the way to go.

---

### Post by mech7 on 2007-05-04
> **nanotube said:**
> i use rdiff-backup
it's a commandline tool, though, i don't know if you are looking for something gui-based.

Yeah i am looking for something with a GUI easy to setup.. with daily backups. In windows there is a simple tool to do this id like something similiar in ubuntu :)

---

### Post by starcraft.man on 2007-05-04
> **mech7 said:**
> Yeah i am looking for something with a GUI easy to setup.. with daily backups. In windows there is a simple tool to do this id like something similiar in ubuntu :)

A back up tool built into windows? What program are you referring to now I'm curious.

---

### Post by psusi on 2007-05-04
tar can do incremental backups.  And you can use crontab to automatically do it every night at midnight.  That's how I set up my server.  Full backup sundays, then incremental each night the rest of the week.  Cron even emails me the results of the backup so I can see that it is or is not working correctly.

---

### Post by mech7 on 2007-05-04
> **starcraft.man said:**
> A back up tool built into windows? What program are you referring to now I'm curious.

Start -> Accesories -> System tools -> Backup

It is a very simple tool but enough for my needs ;) think it only comes with XP pro though.. I thought vista has a better one but can't remember..

I can set it with a gui what kind of backup and how many times it needs to run and which dirs to include.

---

### Post by starcraft.man on 2007-05-04
> **mech7 said:**
> Start -> Accesories -> System tools -> Backup

It is a very simple tool but enough for my needs ;) think it only comes with XP pro though.. I thought vista has a better one but can't remember..

I can set it with a gui what kind of backup and how many times it needs to run and which dirs to include.

Bah, I'm only a home XP user (well, former mostly) so I wouldn't have seen it. I think I know what you want though, look [here]("http://linuxappfinder.com/backupandrecovery/backup") one of these apps must be suitable for you :)

---

### Post by nanotube on 2007-05-04
> **psusi said:**
> tar can do incremental backups.  And you can use crontab to automatically do it every night at midnight.  That's how I set up my server.  Full backup sundays, then incremental each night the rest of the week.  Cron even emails me the results of the backup so I can see that it is or is not working correctly.

oh, really? that's pretty cool, i didn't know that. 
so does it just back up any changed files? does it also keep older versions for possible retrieval? what are the relevant commandline options to look at? 
i'm not gonna switch from rdiff-backup, but it seems like a useful thing to know about tar. :)

---

### Post by psusi on 2007-05-06
I think the switch was -G.  Check the man page.  You give it an index file that notes the state of the files since the last backup.  For a full backup you want to have that file either empty or not exist, so tar backs up everything, then it will create the index file to show what it backed up.  The next backup only backs up files that changed and updates the index.  

If a file changes several times and is backed up in several incremental backups, then yea, you can go back and pull out a specific backup if you want.

---

### Post by siralphred on 2007-05-06
Sbackup does a good job also [http://sbackup.sourceforge.net/HomePage](http://sbackup.sourceforge.net/HomePage)

---

### Post by Done_Fishin on 2007-05-06
Probably not what you are looking for but I use GHOST to back up the whole disk or partition to another disk or partition. Boot from Floppy or CD, select the source disk or partition then the destination disk or partition and copy.

Advantage of a second disk is that you can get up and running quickly in the event of a malfunction due to hardware or software.

Disadvantage is the time it takes to back up OFF system plus if you try to boot from a DISK clone it should have a working grub on it pointing at the partition you selected for boot.

---

### Post by menawollas on 2007-05-06
The problem with Ghost is (apart from the price) that it don't do ext3 or Reiserfs partitions. I believe that the last 'stand alone' version (ie that you can boot from a floppy) is Ghost 2003, and I was playing with this, and Acronis True Image 10 yesterday.

Ghost totally trashed Ubuntu on ext3. True Image will work, but it does funny things with the partition boot sector ie if you installed Grub there, it wont be there on restore, and you have to put it back manually.

The problem (if that is the correct word) with tar and its ilk is that when you restore, it doesn;t blow away all the files that where there before (AFAIK), just replaces or adds the ones from the archive. If there is a way, apart from doing a new install and then using a tar backup, to retsore to a particular point in time, without using imaging software, I'd like to know.

---

### Post by Done_Fishin on 2007-05-06
When I first started to use Ghost (versions 7.5 & 8 ) It recognised my disks and all partitions.
I cloned the whole drive and then when I tried to boot from the cloned drive it just ran the word grub forever across the screen. After a lot of searching I was directed to Super Grub. Thisi allowed me to fix the mbr and I have been booting ever since . I have done this starting with a 40GB drive and just cloning the partitions (swap & install) to a20GB drive. I got the grub problem. Thinking that I had missed  something I grabbed a recently repaired 40GB drive and did a disk to disk. I got the  same problem. I then used Super Grub on the 20GB drive and was able to Boot. Because I ha\d been messing around so much trying to fix the cloned 40GB disk, when I got to the point of fixing the grub, gparted and every partition editor I tried informed me that I had a single disk with unallocated space in spite of the fact that I was booting and using the drive. In XP I could see the swap & linux partition plus 27GB unallocated space. I eventually cured the problem when I used Ghost to copy over the remaining space from the 20GB disk where I had created an NTFS partition and stored my backup from the XP install I have on the other disk. I figure that something got corrupted in the mbr and Ghost fixed it when it added the extra partition, putting it in an extended partition that I had tried to create earlier at the time that things went wrong.
Ghost works fine with my distro's. I aim to add some other distro at some point in the near future since I am trying to get familiar with Linux by "hands on experience":lolflag:

ps I started all this on Ubuntu 6,10 and only after fixing it did I update to 7.04. It's all part of the learning procedure. Make it go wrong but have a back-up so you don't have to worry if you break it!!

---

### Post by hyper_ch on 2007-05-06
You can write your own little backupscript like I have:

[http://ubuntuforums.org/showthread.php?t=434573](http://ubuntuforums.org/showthread.php?t=434573)

Ghost seems to be fine but what if you have to get different hardware? I tend to think Ghost will fail then... for this reason I made myself an install script that will fetch all the software I have installed from the repos :) so all I have to do is a re-install xubuntu, and let that script run and that's it :)

---

### Post by Done_Fishin on 2007-05-06
Very good point.
I would have to go into Windows and use Ghost explorer to extract anything I wanted ( assuming of course that it will show me Linux contents) . I know that people who wrote ERD Commander (name escapes me for the moment) have written some stuff that allows you to read Linux from windows. I thinks it's a freebie too! Not sure how that would work in conjunction with ghost explorer though.
Is there no way to recover a hardware failure in Linux like there is in windows? Must admit I was looking for something using The Live CD

---

### Post by hyper_ch on 2007-05-06
Depends on what you mean by hardware failure?

A ghost image just safes the whole system as it is... when you have to replace hardware you may encounter problems... I can think that replacing the disk drive could render ghost useless as it makes a 1:1 copy of the harddisk/partition...

---

### Post by psusi on 2007-05-07
The problem with ghost, at least the last time I checked, is that it does not understand ext3 or reiserfs, so it just does a sector by sector copy, much like dd.  This means if you restore, it has to be to a partition exactly the same size, and if it is in a different place on the disk, it won't be bootable anymore.  It also makes for a large backup since it copies the free space as well.  

If you want to do a full restore from tar, then you just (re)format the partition.  An mkfs takes very little time, then you just mount and untar.  You can do this from the livecd, then reinstall grub and you've got your system back up and running, even on a different disk/partition.  

Ghost explorer is nice to see inside the ghost image, but again, it won't work with linux partitions since ghost doesn't understand them.  With tar, you can easily extract specific files or the while thing from windows or linux.  The other nice thing about tar is that, as I said before, it can be automated to backup unattended systems and email you the results.  In theory you could have it encrypt the backup and email the backup file itself to you somewhere.

---

### Post by Lucifiel on 2007-05-07
If you want to backup your entire Ubuntu partition, use Partimage. 

[http://ubuntuforums.org/showthread.php?t=287522&highlight=partimage](http://ubuntuforums.org/showthread.php?t=287522&highlight=partimage)

But, for incremental backups, I don't know.

---

