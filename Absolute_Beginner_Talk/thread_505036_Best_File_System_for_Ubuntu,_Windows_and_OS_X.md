---
title: "Best File System for Ubuntu, Windows and OS X"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by PunkRock247 on 2007-07-19
Hello, 

I have a few drives on my network storage machine. I want to move that machine from Windows to Ubuntu. Right now the storage drives (which are separate from the OS drive) are all NTFS. What file system should I use so that all three types of OS can read and write to those network drives? FAT32? Ext3?

Thanks!

---

### Post by skymera on 2007-07-19
Linux and windos both recognise, NTFS, FAT32 etc.

not sure about OS x

---

### Post by FleetAdmiral74 on 2007-07-19
FAT32 I think should work fine. Don't know about OSX...but its so widely used (or was...)

---

### Post by Taino on 2007-07-19
I use Fat32, because I need to access those drives from Linux Ext3-Ext2, WindowsXP/NTFS, and Windows98-Fat32, and Fat32 is easily accessible by all of them, i havent had any issues or problems.

Many data storage device companies use Fat32, They sometimes use Linux and Ext3 on their main OS drive because it houses their OS's (Linux) for the storage device system, But in many cases all of the storage drives within the system used purely to store data are Fat32, i used to work for one and thats how they did it.

But of course it depends on what you will be using to access the machine and those drives with, Fat32 would be the most universal choice.

---

### Post by TopasPV on 2007-07-19
Depending on the filesizes used in your storage FAT32 might not be the right choice because it only supports files smaller than 4GB. I suggest using Ext3 which doesn't have a similar restriction (there's a limit, too but it's far away from what most people need!). Ext3 can be easily accessed by windows-machines through several open source or freeware solutions enabling windows to mount these file systems (just like c:\, d:\, ...).

---

### Post by koganinja89 on 2007-07-19
OMG why doesn't everybody just keep it simple and say: FAT32

Reasons:

 Mac can Read Write Execute from it.

 Linux can Read Write Execute from it.

 Windows can Read Write Execute from it.

EDIT:
-----------------------------------------------------------------------------

You can use NTFS though if you want Bigger Sizes and Smaller Clusters either way GOOD.

---

### Post by PunkRock247 on 2007-07-19
Thanks Everyone. I think I will stick with FAT32. I don't think I have any files over 4 GB. If I run into that problem I will figure it out.

Thanks Again.

---

### Post by shen-an-doah on 2007-07-19
Yep, FAT32 is your best bet. OS X can read NTFS or EXT3, but it can't write to either (as far as I know). Be wary though, Windows won't recognise a FAT32 partition over 38GB.

---

### Post by koganinja89 on 2007-07-19
> **shen-an-doah said:**
> Yep, FAT32 is your best bet. OS X can read NTFS or EXT3, but it can't write to either (as far as I know). Be wary though, Windows won't recognise a FAT32 partition over 38GB.

Yes it can. just make sure it isn't extremely  fragmented or anything like that.

---

### Post by shen-an-doah on 2007-07-19
> **koganinja89 said:**
> Yes it can. just make sure it isn't extremely  fragmented or anything like that.

Really? Because back when I had a 120GB external hard drive, Windows wouldn't recognise it, but Ubuntu and OS X would...

---

### Post by koganinja89 on 2007-07-19
> **PunkRock247 said:**
> Thanks Everyone. I think I will stick with FAT32. I don't think I have any files over 4 GB. If I run into that problem I will figure it out.

Thanks Again.

4gb is for partitions not individual file. JTLYK

---

### Post by koganinja89 on 2007-07-19
well, you were probably using something below XP, where 2000 and below were stupid because they and to have the HD "in" the computer so it could register the NTFS filesystem

---

### Post by shen-an-doah on 2007-07-19
> **koganinja89 said:**
> well, you were probably using something below XP, where 2000 and below were stupid because they and to have the HD "in" the computer so it could register the NTFS filesystem

Nope, it was XP...

---

### Post by koganinja89 on 2007-07-19
> **shen-an-doah said:**
> Nope, it was XP...

Oh, sorry just realized that I said "yes it can" to the wrong thing, I meant that NTFS can be writen to from mac and linux. sorry.

---

### Post by ChaOConnor on 2007-07-19
I realize there are apps to make NTFS work in Linux, but I always thought it was reported they were flaky or something.  Like don't use them to write to NTFS unless you have too, data corruption is likely... stuff like that.

Is that no longer a concern?  If it's not, I'd go w/ NTFS over FAT32, but I only need to share data between Linux and Windows.

---

### Post by Taino on 2007-07-19
> **koganinja89 said:**
> OMG why doesn't everybody just keep it simple and say: FAT32

haha..

yup.. in simple terms...
Fat32, its the easiest to read and write to and from, using Ext3,Ext2,NTFS, and other Fat32 drives.

:popcorn:

---

### Post by koganinja89 on 2007-07-19
> **ChaOConnor said:**
> I realize there are apps to make NTFS work in Linux, but I always thought it was reported they were flaky or something.  Like don't use them to write to NTFS unless you have too, data corruption is likely... stuff like that.

Is that no longer a concern?  If it's not, I'd go w/ NTFS over FAT32, but I only need to share data between Linux and Windows.

you don't need apps of 3'd party sofware or anything like that. just mount it and chmod and chown make sure it is not ReadOnly

---

### Post by ChaOConnor on 2007-07-19
You're right, I mis-spoke.  My question is reading & writing to NTFS: is it as safe as ext3 or FAT32?  Thanks!

---

### Post by AlexenderReez on 2007-07-19
> **skymera said:**
> Linux and windos both recognise, NTFS, FAT32 etc.

not sure about OS x

there is a software for windows to make it recognize ext* partition...

:)

---

### Post by BlahMan_of.Doom on 2007-07-19
:) I was just about to suggest that, although Ext2Fsd has more GUI.

---

### Post by PunkRock247 on 2007-07-20
> **koganinja89 said:**
> 4gb is for partitions not individual file. JTLYK

Well, I formatted one of my drives FAT32 and it looks like Windows XP recognizes the entire thing. I'll let you know if I run into any problems.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=38654&d=1184905878[/IMG]

Thanks

---

### Post by splintercellguy on 2007-07-20
> **ChaOConnor said:**
> You're right, I mis-spoke.  My question is reading & writing to NTFS: is it as safe as ext3 or FAT32?  Thanks!

Yep, it's called NTFS-3G. You can install by doing sudo apt-get install ntfs-config.

---

