---
title: "Need Advice pls..."
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by chinx21 on 2007-06-20
Hi everyone! its me again. I'll share to you my situation right now. I have a new pc w/ the following specs:

• INTEL CELERON 331 2.66 GHZ
• A96MP-C2D MOTHERBOARD
• 64 MB INTEGRATED GRAPHICS PORT
• 256 DDR2 667 MEMORY
• 80 GB WESTERN DIGITAL HARD DISC
• CDRW/DVD COMBO

I'm planning to dual boot my computer by first installing XP and then Ubuntu.
These are the partition that I plan to create..

  TYPE            USAGE                         FILE SYSTEM        SIZE
PRIMARY     WINDOWS                         NTFS                25GB
PRIMARY     WINDOWS PAGIMG/VM     NTFS                 2GB
PRIMARY     LINUX/                               ext3                  5GB
EXTENDED    
LOGICAL      LINUX SWAP                     LINUX SWAP     2GB
LOGICAL      LINUX/ TEMP                     ext3                  3GB
LOGICAL      LINUX/ VAR                       ext3                  3GB
LOGICAL      LINUX/ HOME                    ext3                  5GB
LOGICAL      WIN/ LIN SHARED FILES   FAT32              35GB

USAGE OF MY COMPUTER:
Windows will be use in making reports using word, exel and other office applications, playing games music etc.

LINUX will be use for surfing the net to download files, watch videos

*all files downloaded from the internet such as photos, music files etc. will be stored in WIN/LIN partition omly
*all downloaded freeware, applications will be saved in WINDOWS partition only
*LINUX OS will be use to connect in the internet through a broadband connection

Is there something you can advice to may w/ regard to my partition? I also want to use alternately any of the two OS whenever I want it without shutting down my computer. Would it be possible? 

My future plan is to remove XP after I fully understand Ubuntu. 
Thanks guys!

---

### Post by atria on 2007-06-20
There is no advantage in having a separate partition just for Windows' VM. Just use a single partition for Windows.

I don't see any reason why you'd need so many logical partitions for linux, just create two partitions will do (one for swap and one for /)

There is no need for a shared files partition because you can write to NTFS safely now with linux. Check out ntfs-3g.

Good luck with it ;)

---

### Post by chinx21 on 2007-06-20
fOR better organization and speed-up my computer a bit. thanks anyway? by the way you mention ntfs-3g? what is that and what is the difference between ntfs and fat32. which is better to use?

---

### Post by atria on 2007-06-20
I'm almost 100% sure that doing so will not speed up your computer if you have only one hard disk, heh. Organisation perhaps, but only if you need to backup, say, your /home partition more easily.

ntfs-3g is a new ntfs driver for linux which has write support for ntfs. Stable ntfs write support was not introduced until recently (ntfs-3g)

[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

I personally recommend ntfs for your windows xp partition. It has support for filesystem access control lists and is far more robust than fat32.

---

### Post by molly_001 on 2007-06-20
> **chinx21 said:**
> ... chinx wrote:
 
I'm planning to dual boot my computer by first installing XP and then Ubuntu.
These are the partition that I plan to create..
 
TYPE USAGE FILE SYSTEM SIZE
PRIMARY WINDOWS NTFS 25GB
PRIMARY WINDOWS PAGIMG/VM NTFS 2GB
PRIMARY LINUX/ ext3 5GB
EXTENDED 
LOGICAL LINUX SWAP LINUX SWAP 2GB
LOGICAL LINUX/ TEMP ext3 3GB
LOGICAL LINUX/ VAR ext3 3GB
LOGICAL LINUX/ HOME ext3 5GB
LOGICAL WIN/ LIN SHARED FILES FAT32 35GB
 
.

 
Thanks to 7.04 and the NTFS-3g revolution, partitions can be simplified to the simplest possible construct.  
 
Like you, in the past I used to partition much, with the /home partition, the FAT32 partitions, etc. etc.
 
But thanks to NTFS-3g none of that is now necessary.  You certainly could opt for a FAT32 partition, but it's no longer necessary due to Linux ability to read-write to NTFS.  FAT32 is not secure so be careful with that.
 
For partition planning these days (post Jan 2007) you simply need:
     50GB Win XP ntfs
     29GB Ubuntu 7.04 ext3
     1  GB  ext3 swap
 
I am suggesting a swap larger than is necessary for you, but surely you will add more RAM memory as 256MB will find you slow in Windows.

---

### Post by hyper_ch on 2007-06-20
A seperate /home partition is recommende and maybe also a seperate /boot one... but that just depends on one's own preferences.

---

### Post by chinx21 on 2007-06-20
Thanks Guys!I appreciate it!  Need more advice pls....
But in the meantime, I'll slightly change my previous partition plan which is this:

TYPE USAGE FILE SYSTEM SIZE
PRIMARY WINDOWS NTFS 25GB
PRIMARY WINDOWS PAGIMG/VM NTFS 2GB
PRIMARY LINUX/ ext3 5GB
EXTENDED 
LOGICAL LINUX SWAP LINUX SWAP 2GB
LOGICAL LINUX/ TEMP ext3 3GB
LOGICAL LINUX/ VAR ext3 3GB
LOGICAL LINUX/ HOME ext3 5GB
LOGICAL WIN/ LIN SHARED FILES FAT32 35GB

to this:
PRIMARY WINDOWS NTFS 60GB
PRIMARY WINDOWS PAGIMG/VM NTFS 2GB
PRIMARY LINUX/ ext3 5GB
EXTENDED 
LOGICAL LINUX SWAP LINUX SWAP 2GB
LOGICAL LINUX/ TEMP ext3 3GB
LOGICAL LINUX/ VAR ext3 3GB
LOGICAL LINUX/ HOME ext3 5GB

How can I create  seperate /home partition a seperate /boot?
What are the uses of each?
Install NTFS-3g after install ubuntu?

---

### Post by chinx21 on 2007-06-20
Pls....

---

### Post by chinx21 on 2007-06-21
pls.....help me. I need it now! thanks!

---

### Post by molly_001 on 2007-06-21
You definitely need to read herman's pages on installing Ubuntu using the Alternate Install CD.
 
[Read this]("http://users.bigpond.net.au/hermanzone/"), and you will understand separate /home clearly.  
 
Separate /boot is not a necessity and /boot used as normal is a part of the system file structure that you will access often.  So I prefer leaving /boot inside of /(root)
so that i don't need to change the directory (command: cd) so often.
 
You can install ntfs-3g immediately after installing Ubuntu.
 
However, your partition scheme is still as now farrrrr too complicated.

---

