---
title: "Ubuntu 5.10 Dual Boot...(strange?) sitaution..."
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by RKCole on 2005-12-19
Hello yet again, everyone.

I finally decided that I'd try to install Ubuntu on a dual boot with Windows XP Professional.  I’m not sure what I am doing wrong (as I am sure this problem deals mainly with my Linux-ignorance).

I've tried to search the forums for this situation, among many other Web sites, but I have not found anything.  Let me first give my computer specs (the important ones, anyhow) so then maybe there can be a better diagnosis.

**********
Dell Dimension 4600i
2.80GHz Pentium 4 Processor
Seagate ST380011A 80GB Hard Drive
256MB PC2700 DDR RAM
OS: Windows XP Pro
**********

I used [this tutorial]("http://users.bigpond.net.au/hermanzone/") to try and do this, but to no avail.

Once I reach the option to manually edit the partition table, I see that I have 2 pro/log partitions (I was unaware of this).  The first partition is 41.1MB with the FAT16 filesystem, the second is a 79.9GB partition, and the final is an 8.2MB partition for "FREE SPACE".  I have never partitioned anything on this hard drive in the past...

When I try to edit the 79.9 partition (to size it as stated in the tutorial) nothing happens after entering a smaller size.  Nothing works and nothing is added to the free space.

I am not exactly sure what I ma doing.

Any suggestions?  My main partition (the 79.9GB) uses the NTFS filesystem.

Thanks in advance for any help.

Take care.

---

### Post by tokyovigilante on 2005-12-19
Those partitions store some Dell system utilities which I think you can boot from if you break your computer. I had them on my old 4600i, and wiped them with my first XP reinstall (ah, the bad old days before I discovered Linux ;)). I've never run across a problem that a reinstall of XP or some quality time with a LiveCD couldn't solve, I don't think you'll miss them.

You should be safe to wipe them to free up some of your 4 primary partitions.

What I'd do to set up a dual-boot with XP (if you have the luxury of being able to format your whole disk at some stage) is:

1. Run the Ubuntu installer in expert mode (type expert instead of just hitting enter at the boot prompt). This will enable you to access the partitioner without completing an install.

2. Run through the install accepting the defaults. 

3. When you get to the partitioner, select manual partitioning, delete all the partitions on the disk (till you're left with a single FREE SPACE marker the size of your disk. 

4. Create a FAT32 (we'll convert it to NTFS later) partition of whatever size you want for XP. I suggest 5 gb as a minimum, 10+ if you have a lot of Windows software you still use.

5. Accept the changes, and wait for the partitioner to write a new Partition Table.

6. Exit the installer at this step, then reboot.

7. Pop in the XP cd, and install Windows. The XP installer will ask where to install XP, and you can select the FAT32 partition you created. 
(You need to install XP first as the installer automatically puts the Windows boot-loader onto your Master Boot Record (MBR), and if you install Ubuntu first, its boot-loader will be overwritten and you'll be unable to start Linux. Ubuntu gives you a dual boot option as part of the install.)

8.Accept the installer's offer to convert the partition to NTFS (Quick).

9. Finish the Windows install.

10. Now you have XP on a partition at the start of your disk, and a heap of free space to install Ubuntu to.

11. Reboot and start the Ubuntu install (standard mode is fine, just hit enter at the boot prompt), and when you get the partitioner, select the Automatically Partition Free Space option, and you should be set.

12. Once the main install (part 1 anyway) has finished, the grub installer will pop up. It will tell you it has found XP, and will ask to be installed to the MBR. If you let this happen it will set up dual booting.

13. All set! Enjoy your dual-boot!

If you have any problems let me know.

BTW, on my 250GB drive, I have 4 partitions:
 - 5GB NTFS for XP
 - 20GB / - Ubuntu root
 - ~220 GB /home
 - 4GB swap

I like having a separate /home as it makes reinstalling either OS a breeze.

---

### Post by RKCole on 2005-12-19
Hello, tokyovigilante.

I appreciate the advice, and this path seems the easiest to get this done.  The only problem here, however, is that I have a lot of college data and such on Windows XP.  My wife loves Windows, and she does not really share my enthusiasm for Linux, but maybe after time she will.

I am just stumped as to why the partitioner will not allow me to resize my Windows (NTFS) Partition.  Could this be because there is already a free space partition or something along those lines?  I am pretty software-savvy, but when it comes to hard drive manipulation I know little to nothing. I know how it works and such, but little about doing it.

Is it possible for me to keep the Windows installation the way it is, resize the partition to create more empty space, then partition that space for Ubuntu all through the use of the Ubuntu installer?

I'm quite excited about learning and working with Linux, but my wife would probably kill me if I completely took Windows away.  I want to resize my Windows partition to about 50GB, leaving somewhere near 29GB for Ubuntu, 4GB or so of which would be used a swap space.

But is there some reason as to why the install partitioner will not resize the partition?  Maybe because of already existing free space?

Thanks a bunch for all of the help.

Take care.

---

### Post by Mustard on 2005-12-19
I'm not sure how to proceed with your specific plan..but..

You could install Ubuntu on the 8.2GB of free space.  Its sufficient to get started and muck around learning how to use linux.  I think Ubuntu is going to use 2.4GBs of that space. Its going to take you some time and dedication to fill up the remaining space.

4GB of swap space seems excessive, btw.  I'm only using 431 MBs of swap space myself.  Linux tends to use the RAM to cache stuff, rather than the hard drive.

---

### Post by J_P on 2005-12-19
I only have 40 gb HDD at the moment which was split in half i run winxp PRO first,Then on install of ubuntu i used the default setup and made my way through the options until i get to the partition section,Then i chose to completly write over the my other 20 gig partition(the free one) Then let the disk do its thing i  ended up with exactly what i wanted 20 gig for winxp and 20 gig for ubuntu.
Seems problem free so far!

---

### Post by ubuntuuser on 2005-12-19
You could use a program like Partition Magic to resize your NTFS partition under Windows and then install ubuntu, or you can download a live CD that comes with a program called ntfsresize. Maybe even the recent ubuntu live-cd has this, I'm not sure. Have a look [here]("http://nishants.net/articles/ntfsresize.htm") to learn how to use ntfsresize.
I think gparted can also resize NTFS using ntfsprogs, but maybe you should just boot a live-cd and look if it lets you shrink the partition. If you don't have a live-cd at hand I recommend getting [Knoppix]("http://www.knopper.net/knoppix/index-en.html").

Btw, I have roughly 200 MB swap space and it is rarely ever touched (well, I have three times your RAM ;) ). 4 GB is way too much, I think. An old rule-of-thumb says swap:=RAM * 3.

---

### Post by bscbrit on 2005-12-19
I'm not certain, but I think that under certain circumstances you have to defrag your drive before it can be resized.

---

### Post by mdsmedia on 2005-12-19
[QUOTE=Mustard]I'm not sure how to proceed with your specific plan..but..

You could install Ubuntu on the 8.2GB of free space.  Its sufficient to get started and muck around learning how to use linux.  I think Ubuntu is going to use 2.4GBs of that space. Its going to take you some time and dedication to fill up the remaining space.

4GB of swap space seems excessive, btw.  I'm only using 431 MBs of swap space myself.  Linux tends to use the RAM to cache stuff, rather than the hard drive.[/QUOTE]

I think you'll find it was 8.2MB free space rather than 8.2GB.

I think the reason the partitioning software is stuck is because you already have the maximum number of primary partitions.

I'm not overly experienced with partitioning, but have got stuck with that myself.

One possible method of clearing this up would be to remove the smaller partitions during the partitioning process. I'd proceed with caution, because I'm not an expert and am not sure what the partitions contain or what that might do to the system.

You won't need to get rid of XP completely. The method described above allows you to keep both systems. 

The ideal would be to allow enough space in both operating system partitions to install required software, and leave the remaining space formatted as Fat32, for storage and manipulation of data, which can be read and edited by both operating systems.

---

### Post by Mustard on 2005-12-19
Doh..I just reread the first post.  Hehehe..I can see where I went wrong now. :)

8.2MB is a little small. :)

---

### Post by RKCole on 2005-12-19
Well everyone, I learned quite a valuable lesson today:  Do not delete the 41.1MB partition!!  It is, in fact, a Dell Utility partition.  If it is deleted, Windows will no longer work, period.  I tried everything I could.  But this was somewhat expected for me, so I was prepared.  I reinstalled Windows XP and some other software for protection on it, but doing so I made a separate 25GB partition for Ubuntu!
I did lose a lot of things on my PC, but it was mainly things such as software which I had saved onto a USB JumpDrive.  But on a good note: I have a partition with which I can install Ubuntu!  Looks like things are going better than I had anticipated. (haha)  Wish my wife shared my optimism...but that's just how it goes.

But for Dell users (not sure which model of PC) if you see that partition, it does contain Dell Recovery Utilities...and if deleted, Windows in inaccessible.

Thanks for the input, everyone.  Hopefully I'll have time tomorrow to get Ubuntu up and running.

Thanks again, everyone.  Take care.

---

### Post by tokyovigilante on 2005-12-20
I'm sorry I didn't catch you before you reinstalled.

That Dell partition would've been OK to delete if you'd done it as part of a Windows XP reinstall, as it stores the boot-loader on a dell system, and Windows setup would have recreated it in the MBR. For reference for anyone else, putting in the XP CD, booting to the recovery console and typing FIXMBR would have got XP back up. 

I would have also suggested PartionMagic to resize an NTFS partition, the Ubuntu partitioner can resize NTFS but it must be defragmented, PartitionMagic is much smarter and will shift the data in your partition around so it's safe.

Glad you've now got some space, good luck with Ubuntu!

---

### Post by Lin-X on 2005-12-20
First, this is a great thread, interesting, informative and loaded with possibilities.
I have only a 30 gig drive and a 40 gig. Drive 1 contains a 6 Gb Win98 installation,
a 9 Gb Fat 32 partition, a 510 swap partition, and the rest is Ubuntu, though it takes up only 2 Gb of space, approximately. That middle partition I use as a shared data storage between the two systems. It is Fat32 because Linux can read and write to that, but Windows still refuses to recognize any Linux anything. 
     For a partitioning tool, may I recomend QtParted; it is a Linux program that can
repartition your hard drive without destroying data or trashing your Windows os. It's easy to use and very powerful and can see absolutely everything about your partitions. It is fearless. On the other hand, if you are shy of Linux programs, Partition Magic may help you, but there are some Linux partitions that it refuses to deal with. 
     I know this will seem insufficient to a newbie, but visit Edwards_Enterprises.com and consider getting a copy of a live cd --- Knoppix is the creme de la creme. You pop it into the cd player and it operates entirely from the cd, installing nothing on your hard drive. It has all the utilities you would ever need. I have used it extensively and I am no way a geek. It's the berries!
     Good luck with your Linux. In choosing Ubuntu you have made a very wise decision.

---

### Post by RKCole on 2005-12-20
No need to apologize, tokyovigilante.  It was a lesson well learned, and since I'm in college for computers it gives me more information to use in the world when I find work.  I never knew about that extra partition, so I learned something new from the experience.  I did, however, try to use the recovery console using the "fixmbr" command, but it was to no avail unfortunately.  All is well though because I had many things saved to my USB JumpDrive, so it was all ready to go.

I am actually quite glad that I started this thread, as I have learned quite a great deal here.  I am very glad that I chose Ubuntu because the standards which they uphold are very inspiring.

Thanks for the help, everyone.

Take care.

---

### Post by tokyovigilante on 2005-12-21
I'm pleased you didn't lose too much information. The other thing I would have suggested is to back things up on a USB drive as you have done. A separate FAT32 partition to house all your data is a good option when you're dual-booting, as it will appear as a D: or E: drive in Windows, and you can mount it as /home/<user> in Ubuntu.

Good luck with your install, you've definitely got the right attitude to be successful :).

---

