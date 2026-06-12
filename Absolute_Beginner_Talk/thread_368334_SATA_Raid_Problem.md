---
title: "SATA Raid Problem"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by jakc on 2007-02-23
In regards to my earlier two threads a week ago - [here](http://www.ubuntuforums.org/showthread.php?t=363671&highlight=jakc) and [here](http://www.ubuntuforums.org/showthread.php?t=366133&highlight=jakc) - quick summary - I bought a new 750gb sata 2 drive, wakked it in, somehow managed to blow my graphics card and had problems installing it due to the RAID setup (which I knew little about).  Have now set it to register each device separatley as opposed to seeing them as one drive.  Was going to install Ubuntu on 2nd drive with this partition structure (as advised by Velotix):

> sda1 - /media/win-recovery - FAT32 (Windows Recovery); 5GB
sda2 - /media/drive-c - NTFS (Windows XP); 220GB, with ext2/3 compatibility drivers installed

sdb1 - / - ext3 (Ubuntu 6.10); 80GB
sdb2 - /home - FAT32/ext3/NTFS (Ubuntu/Windows shared access); 10GB
sdb3 - /home/[username]/windows-storage - NTFS (Windows-only Storage); (650GB)
sdb4 - [N/A] (you'll never need to see this drive anyway) - N/A (placeholder primary partition); 1KB
sdb5 - [N/A] (Ubuntu will look for this in a specific place, so don't mess with the default) - swap (Linux swap partition); 3GB

However I have also been advised to install Ubuntu by swapping the drives over (or removing the Windows one) to avoid installing GRUB on sdb (windows drive).  However  my friend who helped me resolve the RAID issue has said that he would not do this as due to the RAID setup he would imagine more problems.  

**What I would like to know is, can I still install Ubuntu (without touching any of my drives) and ensure that GRUB is installed on 2nd drive and sda is untouched?**
i.e. Don't want to unplug anything

---

### Post by tomBorgia on 2007-02-23
Hiya, GRUB will install on your primary drive otherwise you will not be able to choose which OS to boot into (I suppose you could select the other hard disk drive to boot from using your BIOS). I would let the installer install GRUB on your first disk - It will overwrite the Windows boot record but it'll replace it with one for Windows AND Ubuntu. I.e. you can still boot either Windows or Ubuntu with the default GRUB install options.

I know thats not really answering your question, but I think whoever gave you the idea that you need to install grub on your 2nd drive was wrong. Even if you do get problems then you'd just need to boot your Windows recovery disk to recovery console and type "FIXMBR" - This rewrites the master boot record (for Windows to boot).

Sorry, just started deciphering your other threads :) 

> I assume I dont want GRUB installed on sda and like I said in the first post - I want to make this install as simple as possible. Therefore I would like to minimise manual editing of important system-like files such as this GRUB boot loader.

It's all automatic. The GRUB installer will detect your Windows installation and add a entry for it.

You probably don't need 3GB swap - I've been reading a few threads that seem to think if you have over 1GB RAM (I'm assuming...) you don't really need that much swap - probably about 521MB - I think its more important on low-memory systems.

Hope this helps,

Tom.

---

