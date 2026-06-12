---
title: "dual hard drives"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by killaray on 2006-10-31
idk if im missing something but im new to this linux thing and have 2 hard drives installed in my system but in the places>computer folder it only shows 1 drive... is there some kind of command or something i have to do to make it show both drives? if theres a thread already explainin this sorry...

---

### Post by gustolove on 2006-10-31
the directory

//media/

should be the location of any extra Hard drives on the system

check there and if there is nothing listed in there then the other drive is probably not "mounted" which means nothing to you probably but i can explain it if it is the issue.

---

### Post by Belgatom on 2006-10-31
There are quit a lot of threads and not everybody describes their problem the same way. You might be interested in [this]("http://ubuntuforums.org/showthread.php?t=285801") thread. 

In Linux, you have to mount your drive. Although the drive might be physically attached to your system, you have to make this known to your system. 

CD-roms, DVD-roms and USB disk are considered removable media and these are automatically mounted.

---

### Post by jpkotta on 2006-10-31
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by killaray on 2006-10-31
> **jpkotta said:**
> [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

that worked out thanx alot fellas.. now i used that automaticallymountpartitions link, and it made my HD read only.. how do i change that?

---

### Post by Belgatom on 2006-11-01
I fished this out of the forum a few days ago. 

> 1. press ctrl-f2 and type 'gksudo nautilus'
2. enter your password
3. in the nautilus window that opened browse to your external drive and make a new directory
4. right-click on the new directory's icon, select 'Properties' and on the 'Permissions'-tab change the directory's owner & group to your user.
5. Close the nautilus window, it's running with root permissions and you don't want to have it open if it's not absolutely needed as you can easily break your system with it..

If your disks are NTFS, this will be a bit more difficult. I will leave this up to the experts.

---

### Post by killaray on 2006-11-01
my disk is NTFS... and where do i hit ctrl+F2? just anywhere randomly?

---

### Post by bulldog on 2006-11-01
> **killaray said:**
> that worked out thanx alot fellas.. now i used that automaticallymountpartitions link, and it made my HD read only.. how do i change that?

FYI NTSF file system is read only.
You can copy and paste from it but can't write anything to your disk.

There is a solution for this,but writing to a NTFS file system is not recommended by Ubuntu.

---

### Post by Belgatom on 2006-11-01
I assume the Ctrl+F2 is supposed to open the terminal. At least, that is what I assumed when it didn't work. So, I opened it manually and did the rest.

---

### Post by killaray on 2006-11-01
y is it only read only? it worked fine in windows... or is it only read only for ubuntu?

---

### Post by Belgatom on 2006-11-01
I am sure you can find lot's of information about a basic fact like linux filesystems but here it is in a few lines.

Windows used to use Fat32 as a filesystem.
When XP came along, you had the choice: Fat32 or NTFS.
NTFS is preferred due to it's stability. 
Windows can not read Ext3.

Linux uses Ext3 to store information on disks.
Linux can read Ext3, Fat32 and NTFS.
Linux can write to Ext3 and Fat32.
Out of the box: Linux can not write to NTFS.

There are however adaptions you can use to be able to write to NTFS but make sure you have a backup of the info on the NTFS disk you are going to write to.

At to "Y". Read up on the history of Linux.

---

### Post by louieb on 2006-11-01
[LIST]
[*]I have a P2 400MHZ 384MB ram and an old award bios that crapes out and refused to boot if a hard drive greater that 33 gig was installed.
[*] I found this out when I installed a 40 gig Maxtor a second drive. I have two options with this drive one is to upgrade my bios the other is to set the capacity limiting jumper (CSL) on the drive. When the CSL is set the drive reports to bios that it is a 33 gig hard drive, bios is happy and the machine boot up just fine. 
[*]The primary drive on this PC is a 30 gig WD drive with Ubuntu installed.
[*]The slave drive had XP installed. (The Maxtor described above). 
[*]The problem I had with this setup is that Linux (first Fedora 5 now Ubuntu) is thoroughly confused by this set up. Both reported The drive had two partitions an 8 gig NTFS partition and a 32 gig unformatted partition. 
[*]I never did get Linux read the second drive. I finally replaced it with a used 8 gig drive and installed XP on it. 
[*]When Ubuntu booted after the 8 gig drive was detected and an icon sits on my desktop and I can read files on the drive. 
[*]The Maxtor drive now sit in an old P3 e-machine and holds half a dozen Linux distributions. And I have full use of all 40 gig on the drive.
[*]I guess the point of this is there are weird hardware setups that even Linux cannot figure out.
[/LIST]

---

### Post by killaray on 2006-11-01
> **Belgatom said:**
> I am sure you can find lot's of information about a basic fact like linux filesystems but here it is in a few lines.

Windows used to use Fat32 as a filesystem.
When XP came along, you had the choice: Fat32 or NTFS.
NTFS is preferred due to it's stability. 
Windows can not read Ext3.

Linux uses Ext3 to store information on disks.
Linux can read Ext3, Fat32 and NTFS.
Linux can write to Ext3 and Fat32.
Out of the box: Linux can not write to NTFS.

There are however adaptions you can use to be able to write to NTFS but make sure you have a backup of the info on the NTFS disk you are going to write to.

At to "Y". Read up on the history of Linux.

thanx for the linux lesson... idk if im going to stick with Linux for now... need to do to many alterations and i have little time.. maybe 1 day when i have time ill take this up... anywho, how do people have dual boot systems if linux cant write on NTFS? do they have to redo everything on FAT32 before they can have a dual boot system?

---

### Post by mattskr on 2006-11-01
> **killaray said:**
> y is it only read only? it worked fine in windows... or is it only read only for ubuntu?

It will still work fine in Windows...

Because the developers working on NTFS support have not perfected writes to NTFS drives, so writes are disabled.

I did read somewhere recently though that they did get it working, but I don't think it's built-in yet, and I couldn't find the stupid article.

---

### Post by killaray on 2006-11-01
should i stick around? i mean if i can get my dual monitors goin and my internet sharing i would be fine.. i can live wit not being able to write to the drive for a bit

---

### Post by mattskr on 2006-11-01
> **killaray said:**
> thanx for the linux lesson... idk if im going to stick with Linux for now... need to do to many alterations and i have little time.. maybe 1 day when i have time ill take this up... anywho, how do people have dual boot systems if linux cant write on NTFS? do they have to redo everything on FAT32 before they can have a dual boot system?

You can have different types of filesystems on one drive (each partition can have it's own drive) So one partition in NTFS for XP, one in ext3 for Linux and I usually like to have a FAT32 partition so I can share files between XP and Ubuntu on the same machine.

---

### Post by killaray on 2006-11-02
i didnt know u can have different filesystems per partition.. anywho i guess ima stick around for a while... i have 1 question though, whenever they update Ubuntu, will all the edits i've done to it stick around? or will i have to go threw it again?

---

