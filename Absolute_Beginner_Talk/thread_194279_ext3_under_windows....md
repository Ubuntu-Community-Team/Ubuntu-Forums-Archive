---
title: "ext3 under windows..."
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by kakashi on 2006-06-11
hi guys. i did not know which section to put this in so i placed it here. if this is wrong please tell me and i'll pm a mod. 

anyway i need to use windows for oblivion and other games. but i need ubuntu cuz i HATE using windows for anything else. ok another point is a am alway downlaoding a lot of stuff using bittorrent. so i need a shared parition that would allow me to dl under both linux and windows. i found the fat32 format does not support large partitions ( i am making one of 167 GB) and ntfs write suppot is difficult to get under linux. so i thought i'll use ext3. i found ext2ifs to install in windows. 

So far i've had only 1 major problem cuz i crashed the computer (overclocking the video card). So windows did not run any check it would normally but i resolved that by running fsck in linux. 

so this was my reveiw part. 

now the question. 
Do i need to deframgment the filesystem. if so HOW.
also does anyone know any i'll effects of this activity on my data and hardware?

---

### Post by olsonar on 2006-06-11
There's a program called defrag in the repos for defragmenting.

---

### Post by aysiu on 2006-06-11
I don't know anything about ex2ifs, but I've had no problems using [http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by olsonar on 2006-06-11
aysiu, that is ext2ifs. it's what i use, and works perfectly for me as well.

---

### Post by Solver on 2006-06-11
[QUOTE=aysiu]I don't know anything about ex2ifs, but I've had no problems using [http://www.fs-driver.org](http://www.fs-driver.org)[/QUOTE]

For write access, too? I am using Explore2FS, which only gives read-access, but may switch to FS-driver, if it's safe for write.

---

### Post by aysiu on 2006-06-11
FS-drive has perfect write-access on my computer.

---

### Post by 5-HT on 2006-06-11
[quote=Solver]For write access, too? I am using Explore2FS, which only gives read-access, but may switch to FS-driver, if it's safe for write.[/quote] [quote=aysiu]FS-drive has perfect write-access on my computer. [/quote] 
Thanks for input aysiu. 
Nice to know you haven't had any problems writing with Ext2IFS.

I'm looking for ext3 support under Windows and Solver kindly suggested Explore2FS (read access).

Maybe I'm too paranoid about data integrity, but this portion of the FAQ for Ext2IFS caught my attention: [quote=http://www.fs-driver.org/faq.html]
**Does the Ext2 driver access Ext3 volumes, too?**

            The *Ext3* file system is the *Ext2* file system which has been extended by *journaling*. Ext3 is backward-compatible to Ext2 - an Ext3 volume can be mounted and used as an Ext2 volume. Just as older Linux Kernels which do not know the Ext3 file system can mount Ext3 volumes (as Ext2 volumes), the Ext2 file system driver ext2fs.sys for Windows incorporated in this software package can do it without any problems, too. Of course you do not take advantage of the journaling of the Ext3 file system if you mount it as an Ext2 file system. 
              Journaling keeps the file system of a volume consistent, even though the volume has not been cleanly dismounted in the past (for instance because the computer has crashed): There is no need for running e2fsck (the "chkdsk" of the Ext2/Ext3 file system on Linux). [/quote] 


Hopefully fsck would fix any possible problems that could arise after a hardcrash during write, but it is nice to have a journal. 
Just thought I'd add this here as I haven't seen it discussed in any threads that I've come across on the matter.
Sorry if it was already obvious to anyone else.

---

### Post by stubbe on 2006-08-24
This thread caught my attention. I also uses ext2ifs driver and it works like a charm. My only concern is that there's no tool to check/fix ext2/3 partition under windows. I have alot of bad experiences in using FAT32 for connectivity. So is there any tools to check ext3/2 integrity under windows?

Another alternative is to use Captive-ntfs which provides full NTFS support with integrity checking support. Been experimenting with Captive back then and I should say it's flawless. But this would be my second alternative, since if something happens with the NTFS partition, well, live distros probably can read it somehow, NTFS is much closed (duh!) than linux filesystems.

---

### Post by Beliar on 2006-08-29
Hi, I know this is not an ext2ifs support forum (but there is none :P).
For me, it doesnt work that well :(
After installing ext2ifs i could read and write my ext2/3 partitions, but suddenly i couldnt access my windows D: (ntfs) partition anymore! After deleting the drive letters with the ext2ifs mount tool, it still didnt work. Only after uninstalling the whole driver i could access D: again (all data still intact).
But it would be really nice to be able to read ext2/3 x(
Anybody facing the same problem, or anybody an idea what it might be?

thx & greets,
Beliar

---

### Post by orbital on 2006-08-29
I've been using ext2ifs for a while now without any problems. Now suddenly I can't access my ext3 partition anymore from Windows. My partition shows up but I can't access it. Re-installing the software didn't help either. Everything works like a charm with Ubuntu.

What to do??

---

### Post by Beliar on 2006-08-29
i dont understand why that guy who developed ext2ifs didnt make a Forum or a Mailing list for people who have problems, questions or suggestions to his program. :(

Is he at all working still on it, or is it abandoned? (Last release from 2005)

---

### Post by orbital on 2006-08-29
Now my ext3 partition seems to be working fine again. Strange...

---

### Post by magicw on 2006-09-02
I am also using ext2ifs (1.10) but am experiencing some problems!  When trying to access some directories (not all) on an ext2-linux file system from windows the computer tells me that the file system is corrupt.  

Some more facts that might help:
1. If I run fsck on the ext2 file system, it does not report any problems.  However, once I have tried to open any directories of the filesystem from windows fsck has to repair the file system on reboot into ubuntu
3. The file system in question is about 120 GB.  Another ext2 file system with 10 GB on the same hard disk works fine.

Any ideas?

---

