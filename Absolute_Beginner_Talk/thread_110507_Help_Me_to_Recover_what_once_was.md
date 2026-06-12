---
title: "Help Me to Recover what once was"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by Purplexus on 2005-12-30
Well Okay Absolutely New to Linux/Ubuntu

I Had a Storage Drive of 250 GB which contained Pictures and Mp3's Using NTFS
I have done a lot fo research through this site to see how i mount the drive okay Done

One site suggested I mount it using the Dir Media/Windows  (why Not)
regardless I used some Unmask command  (I'll figure out what this does later)
Okay Everything should be fine...  EXCEPT!!!!

It says my 250 GB Drive has 232 GB FREE!!!(It Never did recognize the entire 250GB)    .... Oh My GOSH!
I can live without the Mp3's  But some of the photos.... YIKES!

I just got married... am I about to be divorced.. Our Wedding photos were on that disk??? (they are backed up on DVD using a backup program that was windows based.. I hate Windows)

Or... Can someone show me how to recover the data that once was on that 250 GB Disk

PLEASE SOMEONE SAVE MY MARRIAGE!!!!!

---

### Post by kaamos on 2005-12-31
:shock:

If you have not enabled writing to ntfs by installing additional drivers that can enable this, your data can only have disappeared due to a error in the filesystem. Or more precisely: in my opinion your data should be safe. Perhaps defragging the drive or whatever tools windows has for tidying up ntfs volumes might help. Have you checked from a windows machine what shows on the disk? Because the drive could be just mounted with wrong options in linux..

Truly hope you get your stuff back.

---

### Post by Purplexus on 2005-12-31
Actually I am Trying to go 100% Linux So I never want the windows back if possible.

I will now research how to Get the drivers that you are talking about  I hope this works.

Btw.... I dont get anything returning when I Enter the command Fdisk -l in my terminal?

---

### Post by kaamos on 2005-12-31
[QUOTE=Purplexus]I will now research how to Get the drivers that you are talking about[/QUOTE]
Bad idea! My point was that if you have **not** installed these drivers you should be safe.

Writing to ntfs is not stable in linux yet.

---

### Post by Purplexus on 2005-12-31
okay those drivers are not installed nor i have i installed them

So.....   Is there a disk recovery tool where i can recover the missing info?
or.... do i have to go back to windows and recover them seperately????

(meaning i have to reinstall windows :(         )

---

### Post by Sirin on 2005-12-31
> I Had a Storage Drive of 250 GB which contained Pictures and Mp3's Using NTFS

Bad idea. Linux hasn't mastered full NTFS support yet. Try using FAT32 (There may be some sacrifices, but if you don't mind losing the Integrated Compression tools (Not Windows Zip, but the Zipless-Compression feature) or the Encryption Tools (That aren't actually that safe, trust me), then you should have no problems with FAT32).

> **Purplexus]
It says my 250 GB Drive has 232 GB FREE!!!(It Never did recognize the entire 250GB)    .... Oh My GOSH!
I can live without the Mp3's  But some of the photos.... YIKES!
[/QUOTE]

Which means you have only used up 18GB of your HD space.

> 
I just got married... am I about to be divorced.. Our Wedding photos were on that disk??? (they are backed up on DVD using a backup program that was windows based.. I hate Windows)

If it is an .exe on the DVD that is needed to start the recovery process, then yes, Windows is the only way. If the files are seperate, then you may try on Linux, but make a backup of your DVD files, in case you accidentaly muck up something.  said:**
> 
Or... Can someone show me how to recover the data that once was on that 250 GB Disk

Temporarily install Windows, run the backup program, get your files back, 

> 
PLEASE SOMEONE SAVE MY MARRIAGE!!!!!

If I am correct, your wedding should be on the DVD, no? If so, all is not lost. :)

---

### Post by ormus on 2005-12-31
you can try the knoppix live cd. it rescues most things that others cannot, in my experience.
knoppix mounts the hdd automatically, my ubuntu doesnt.

---

### Post by Stroganoff on 2006-03-18
[QUOTE=Sirin]Bad idea. Linux hasn't mastered full NTFS support yet. Try using FAT32 (There may be some sacrifices, but if you don't mind losing the Integrated Compression tools (Not Windows Zip, but the Zipless-Compression feature) or the Encryption Tools (That aren't actually that safe, trust me), then you should have no problems with FAT32).[/QUOTE]
Do not use FAT32! That Filesystem is slow, unstable and can't handle large files > ~5GB.
Use Ext2 instead. There are fully functional Ext2-Drivers for Windows (your friends may use it).
I suggest this one, it's free *as in beer*.

**Ext2 Installable File System For Windows**
[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

Advanced users would like to try [this one](http://ext2fsd.sourceforge.net), OpenSource.

My USB hard disk has got one 100MB-FAT32-partititon with those setup-files and one large xxxGB-partition with my *data* stored under [Ext2](http://en.wikipedia.org/wiki/Ext2).

---

### Post by adamkane on 2006-03-18
If you want to save your marriage, then add the Windows drive as a second drive to a Windows computer, and transfer the files over a local network to your Ubuntu computer. You probably need to buy a second drive for the Ubuntu machine, if you don't have enough room. Once you are done transferring the files, you can format the old harddrive as ext3, and you can forget about Windows.

---

### Post by aysiu on 2006-03-18
[QUOTE=ormus]you can try the knoppix live cd. it rescues most things that others cannot, in my experience.
knoppix mounts the hdd automatically, my ubuntu doesnt.[/QUOTE] I second the motion on Knoppix. Use Knoppix to copy your important files to blank CDs, blank DVDs, an external hard drive, an iPod, a million floppy disks... whatever you have for backup.

---

### Post by dueY on 2006-03-18
The easiest way you are going to fix this is by having another harddrive that boots Windows handy.  Slave your messed up harddrive.  Boot from the Windows drive and download a data recovery program (there are some out there for free or atleast trial).  Just make sure you don't install anything or write to your harddrive you're trying to recover.

---

### Post by IYY on 2006-03-18
I'm a bit confused about your problem. Have you tried mounting the drive from within Linux and failed? Why are you so sure that Linux won't be able to read your NTFS files?

In order to mount an NTFS partition or drive:

Make a directory called /media/windrive (**sudo mkdir /media/windrive**).

Go to System > Administration > Disks, enter your password. Find your 250 GB disk, go to the Partitions tab, select the partition you want to browse (you may only have one), and type **/media/windriv**e in the Access Path textbox. Then click on the Enable button.

Now, start a root shell and browse the new drive. In a terminal:

sudo bash
cd /media/windrive
ls

See what files are on there. If you find the files you want, just copy them to your home directory. Ubuntu should be able to read all the files on your NTFS partition.

---

### Post by verbalshadow on 2006-03-18
Two Ideas

1) I would try [UBCD for Windows]("http://www.ubcd4win.com/") its a liveCD that is windows based and has admin recovery tools included. The downside is that you can't just download a ISO.

2) Buy a external USB harddrive case and take it over to a friends house that has burner and windows,

---

