---
title: "Win 7 dual boot possibilities"
date: 2013-01-20
forum: Any Other OS
---

### Post by MadmanRB on 2013-01-20
Well today I got my copy of windows 7 back from my old house and now I may redo a dual boot in the near future considering my attempted install of windows 7 in virtualbox did not work as well.
So I am thinking of dual booting again but this time doing something new and different.
This time I wont devote half the drive to windows as I barely booted into it, but I still may want to have it around to just play around with.
I have two main drives, a 640GB hard drive and a 1TB hard drive.
I am thinking of making my 1TB totally dedicated to NTFS and possibly using it as sort of my home directory for Linux as NTFS is a file system both operating systems can read/write to NTFS.
So now I am debating on how much room to devote to win 7, after all why give it more room when its not the primary OS?
Sure I did say that the 1TB drive will probably be devoted to NTFS but it will only be used as a storage drive not a drive for the OS's
I am thinking of dedicating at least 50GB to Linux as that allows me room to have a primary root partition and a small home directory, say about 20GB for root and the rest for home and dedicate the rest for windows as windows being a space hog will need the room I can provide.
I may give more space to linux but as I said the move to NTFS for file storage may aid on my growing space issues.
So yeah I am still giving more room for windows, but linux being so small and being compatible with NTFS still will make it my primary OS
I would split the primary drive but why bother when linux can run just fine even with small space limitations

---

### Post by sudodus on 2013-01-20
If I understand correctly, you plan to use the 1 TB drive as a data drive running the NTFS file system, and to have both Windows and Ubuntu on the 640 GB drive.

This should be no problem. But if you plan to use Ubuntu as the main system, I would give it more than 50 GB (not even 10% of the drive). At least as long as the data drive has NTFS, because the linux drivers for NTFS are rather slow, and you cannot manage individual file permissions from linux on that file system.

An alternative might be to use an ext3 or ext4 file system on the 1TB drive and to install software to read ext file systems into Windows. See this link

[http://sourceforge.net/projects/ext2fsd/]("http://sourceforge.net/projects/ext2fsd/")

---

### Post by MadmanRB on 2013-01-20
Yeah I am aware there is software that can read ext3/4 on windows, but it doesnt give full access.
Like what if I wanted to listen to music while in win 7, an ext3 partition will cripple that ability.
And truth be told I never had too many issues with Ubuntu and NTFS, because my disks are internal drives not external ones and both run at decent speeds.
But yeah I will consider more than 50GB for linux, maybe jumping it up to half the drive.

---

### Post by oldfred on 2013-01-20
I install Ubuntu to 25GB root partitions including /home but have all data in data partitions. I still have data in my NTFS for sharing with XP but now do not use XP and most new data goes into my Linux formatted data partition. I even moved Firefox & Thunderbird profiles to the NTFS so I have the same bookmarks & email in all systems.

You cannot use NTFS for /home, but can link folders from any partition back into /home.

       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

    
       Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Mount NTFS partition:
[http://ubuntuforums.org/showthread.php?t=1927504](http://ubuntuforums.org/showthread.php?t=1927504)

---

