---
title: "Some basic daily operations."
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by Stone_Wolf on 2005-12-07
Hiyas again

Just some simple questions i hope you all can give me a howto on. I'd like to know some simple stuff, daily routines that are just handy to know.

1: How to check disk space?
   e.g.  "df -T -h"  (Found in the wiki)

2. Do a scandisk, checkdisk or whatever the alternative is?

3. Defragment the drive? Is there even an option, and are they different for different filesystems?

I'd prefer to do this all from the terminal, but if there are some GUI ways of doing it others would prefer, then please supply them also.

Thanks again
SW

---

### Post by cwaldbieser on 2005-12-07
[QUOTE=Stone_Wolf]Hiyas again

Just some simple questions i hope you all can give me a howto on. I'd like to know some simple stuff, daily routines that are just handy to know.

1: How to check disk space?
   e.g.  "df -T -h"  (Found in the wiki)

2. Do a scandisk, checkdisk or whatever the alternative is?

3. Defragment the drive? Is there even an option, and are they different for different filesystems?

I'd prefer to do this all from the terminal, but if there are some GUI ways of doing it others would prefer, then please supply them also.

Thanks again
SW[/QUOTE]

1. You are correct, diskspace remaining can be found by issuing "df" (disk free) in the directory you want to measure.

2. fsck (file system check).  The drive you want to check has to be unmounted, first.

3. No defragging necessary for ext2, ext3, ReiserFS.  Fat32 needs to be defragged, but you usually do it from Windows-- not sure how to do it from Ubuntu.

---

### Post by r4ik on 2005-12-07
Every 30th time the machine starts up it scandisks auto.

---

### Post by GreyFox503 on 2005-12-07
2.  The closest thing to scandisk is "fsck" (I think its file system check).  There's no need to run it unless you're having problems with something.  I think that if you use ext3, then every 30 boots or so, it automatically does this anyway.  That kind of annoyed me, so when I installed again I choose reiserfs.  Haven't checked it since, and it works fine.

If you run fsck, BE SURE TO UNMOUNT THE FILESYSTEM FIRST. :)

3.  You don't need to defragment either.  If you're using ext2, it is possible to defrag it, but so unimportant that the program doesn't even come installed.  I'm pretty sure that you actually cannot defragment an ext3 or reiserfs partition.  Fragmentation on all these file systems is kept to a very minimal level automatically.


I think that daily maintenance of my Ubuntu system is easier than a Windows system.  No anti-virus scans, no spyware scans, no registry cleaners, no defragmentation.  The only real system maintenance I do are regular backups.

---

### Post by Stone_Wolf on 2005-12-07
Hiyas again

And there be the crux of my problem. I'm using a FAT32 partition on my secondary drive as it's shared between two other machines. I know it's  still a little advanced for me right now, but i'm trying to give two or more windows machines read/write access to the shared FAT32 drive over the network. I'd just like to know how to defrag that every so often in Ubuntu as it'd be a pain in the proverbial if i had to take it out and slap it into a windows box to defrag once a month or more.

Regards
SW

---

### Post by cwaldbieser on 2005-12-07
[QUOTE=Stone_Wolf]Hiyas again

And there be the crux of my problem. I'm using a FAT32 partition on my secondary drive as it's shared between two other machines. I know it's  still a little advanced for me right now, but i'm trying to give two or more windows machines read/write access to the shared FAT32 drive over the network. I'd just like to know how to defrag that every so often in Ubuntu as it'd be a pain in the proverbial if i had to take it out and slap it into a windows box to defrag once a month or more.

Regards
SW[/QUOTE]

If no Windows partition uses it natively (i.e. you don't have Dual Boot PC), then you should make it an ext3 or a ReiserFS filesystem.  When you run Samba, the Windows clients communicate with the Samba server over the SMB protocol, but the OS running the server is the software that actually writes to the filesystem.  Put another way:

```

Win95 client <----- SMB Protocol ------> Ubuntu w/ Samba <---> ext3 filesystem

```

---

### Post by Stone_Wolf on 2005-12-13
Oh right! Silly me >.<

I forgot that happens, sort of the same way Win98 is able to see NTFS partitions over a network. Thanks for the reminder, that'll save me a lot of headaches. ;o) As they say, "It all gets lost in the translation"...or something along those lines.

Regards
SW

---

### Post by nocturn on 2005-12-13
For Ext3, fsck will run automaticly at intervals, no need to force it.  Reiser does not need this.

There is no need to defragment drives on either filesystem.

---

