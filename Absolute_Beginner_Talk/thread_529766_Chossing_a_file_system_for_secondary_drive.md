---
title: "Chossing a file system for secondary drive"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Aishiko on 2007-08-19
OK I have several questions, I'm leaning toward making the new 500gig HD a Ext3 formated media storage hard drive, but before I do I would like to hear how well the XP drivers to read and write to this particular file system.  I also wonder if there is a way to make WinSever 2003 (which is the worse OS I've ever used, randome restarts, blue screens of death, system instablity, unable to end programs, etc.  Oh and when trying to use it as a file server it doesn't even do that! the other 2 (ok 4 if you include laptops) windoze PCs can see it but can't access the shared folders/drives/files.) be able to read ext3 file systems?  what are the chances of a failure ruining a file on a ext3 when copying/moving or otherwise messing with the file from a Windoze computer?  Because I hear that there is a chance of a failure when runing a file from a NTFS file from Linux though I have never been told the particulars or ever meet anyone that that has happened to.

Second, does anyone have experience sharing a storage drive on a network under 6.06.1 or 7.04 desktop editions?  To Windoze and other Linux computers?  I'd use my USB 2.0 laptop drives turned into portable USB storage but only 1 computer has USB 2.0 capabilities so that takes forever when transfering files from the main PC to the PC with the DVD Burner (I'd like one maybe for the winter holidays or after I see what extra money I have after I pay for the next semester's classes, heck I'd like a new laptop from hypersoinc, ahhh to dream).

For Now I'm going to have a Windoze computer for those programs that are not Linux native or run too slowly under WINE on my old dual 700Mhz computers, the other.. well It's Ubuntu.

---

### Post by moredhel on 2007-08-19
The drivers I use for XP are perfect :)

---

### Post by Aishiko on 2007-08-19
Thank you  that is 1 question down just have what 3 million more to go? :P seriously, that really just leaves setting shared files/folders/drives/directories in Ubuntu to other computers running Windoze and other Ubuntu computers, and what is the worse case should the drivers fail inthe read/write process.

Oh and Moredhel what drivers do you use?  did you get it from sorceforge, or fs-driver, or some other repository?

---

### Post by annda on 2007-08-19
i've been using the ext2fs driver for some 5 years now and it has never caused me any troubles - but then i've used the 'write' options only 2-3 times. various distributions of linux have been my main os's, so it was mostly reading data.

potentially, you could compromise the whole partition so if you have more users on the network, it might be good a to have the old vfat (FAT32) system on a shared disk. or maybe someone around here has more experience and a better idea...

---

### Post by HereInOz on 2007-08-19
Consider using an NTFS partition.  There is an application called ntfs-3g (in the repositories) which allows Linux to read and write to NTFS partitions.  You have far more chance of getting Linux to reliably read a Windows partition than you ever have of getting Windows to read and write to an ext3 partition.

Microsoft is just not interested in interoperability.

Also, FAT32, or VFAT, is not particularly good for large drives.  Ntfs-3g is now stable and is possibly your best choice.

---

### Post by Aishiko on 2007-08-19
OK I was thinking of using Linux to read and write to this drive and then use Windows to burn the files to DVD peroidiacly for back up purposes and maybe to play media files over the network on XP or Ubuntu.  So I think I'll make the 500 giger a NTFS partition and try out EXT3 or some other file system on a smaller harddrive first.  Perhaps a 40gig.  From what I understand Linux right now can read NTFS OK, but the write feature has a potential to do bad things?  but it sounds like that potential is rather small, is that right?

---

### Post by louieb on 2007-08-19
Just my two cents worth. Use the file system that is native to the OS the drive will be plugged into  the most. That is  if the drive is going to be plugged into a PC running Linux then by all means format it ext3.  If your going to plug it in mostly on a Windows PC then NTFS is the way to go. 

As others have said there is software you can install on both Linux and windows to allow reading and writing to a file system made for the other.

---

### Post by Aishiko on 2007-08-19
> **louieb said:**
> Just my two cents worth. Use the file system that is native to the OS the drive will be plugged into  the most. That is  if the drive is going to be plugged into a PC running Linux then by all means format it ext3.  If your going to plug it in mostly on a Windows PC then NTFS is the way to go. 

As others have said there is software you can install on both Linux and windows to allow reading and writing to a file system made for the other.
Yeah, I was thinking the same thing but, I was having a hard time deciding which OS to have it run under (I have a Windoze Pc and a Linux PC) but trying out Linux again I think I'll put it under Windoze until I've given this new generation of Linux a fulltest drive.

---

### Post by moredhel on 2007-08-20
[http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/)

^ I've used that driver for about a year and a half, with quite a bit of writing tasks, not just reading.

---

### Post by kellemes on 2007-08-20
> **HereInOz said:**
> Consider using an NTFS partition.  There is an application called ntfs-3g (in the repositories) which allows Linux to read and write to NTFS partitions.  You have far more chance of getting Linux to reliably read a Windows partition than you ever have of getting Windows to read and write to an ext3 partition.

Microsoft is just not interested in interoperability.


On the contrary, NTFS is closed source and although now seemingly supported it took a very long time and **it is still a strong beta** eventhough it may work for people without issues.
etx2/3 is open source and supported by several drivers for the Windows platform. This has nothing to do with MS being interested (or not) in interoperability, this has to do with developers being able to study ext2/3-code and develop working drivers for it.

---

### Post by TeaSwigger on 2007-08-20
I've been using the ext2fsd driver in Windows 2000 Pro ( [http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/) ) for both reading and writing to a shared ext3 partition, including heavy use with graphic and temp files (Photoshop). It works perfectly. Furthermore, in the event of a problem, data can be recovered better from a journaling filesystem, which discouraged me from using old fat32. The fact that there are many open source utilities and support for doing so makes ext3 a good choice over ntfs from that angle as well. So I chose ext3.

---

### Post by louieb on 2007-08-20
> **Aishiko said:**
> OK ...
Second, does anyone have experience sharing a storage drive on a network under 6.06.1 or 7.04 desktop editions?  To Windoze and other Linux computers? 

For Linux to Linux I run ssh-server running on the host . Then on the client its Places>Connect to Server>SSH. Pretty easy.  

For Linux to Win. Pretty much the same Places>connect to server>windows share. 

For Win to Linux I set Samba. Should be easy but sometimes I have to do a little digging to tweak it. When using the 7.04 GUI just make sure the workgroup name is correct before setting up the share.

---

### Post by Aishiko on 2007-08-20
thank you all for the advice but TeaSwinger has me wondering is EXT3 a journalling system and I read in another thread taht journaling systems can slowly eat up space in "invisiable" files used exclusively for the journalling process.

---

### Post by Ek0nomik on 2007-08-20
> **Aishiko said:**
> thank you all for the advice but TeaSwinger has me wondering is EXT3 a journalling system and I read in another thread taht journaling systems can slowly eat up space in "invisiable" files used exclusively for the journalling process.

Yeah, they will eat up some hard drive space.

Although I am quite positive you can reduce the percentage of the disk allocated towards this.  For some reason I can't find any links about the matter though...

Perhaps someone else can find some?

---

