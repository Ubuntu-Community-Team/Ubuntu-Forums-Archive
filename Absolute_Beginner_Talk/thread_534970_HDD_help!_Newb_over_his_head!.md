---
title: "HDD help! Newb over his head!"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Aiello on 2007-08-25
Gah! 
Ok, I am having some seriously nerve racking problems right now.
I was going to install Ubuntu along with Windows XP for a duel boot system. Now, this is a family computer, so I only wanted Ubuntu to have 13gb or so. The auto-partitioner in the installer did not allow me to set it that low. So, I had to manual partition. I guess I messed up some how because I got some errors when I went to hit forward. I then consulted the the forums for help and some one told me to go into gparted and decrease my Windows partion. They then told me to hit the button in the installer that said for Ubuntu to use the largest free space. Everything seemed to be okay until it wanted to know if I wanted to import anything from my Windows account. I selected a few things like My Documents, filled out the info for the new Ubuntu account, and clicked forward. The loading symbol appeared on the cursor, but there was no disk activity. I didn't think much about it, so I left the computer to do its thing and went out for dinner. I got back about 4 hours latter and it was still on the same screen (data transfer page with loading icon and no disk activity). Figuring some Windows data might have been corrupted in the partitioning, I exited out of the installer and exited out of the Ubuntu LiveCD. I booted back up Windows XP and it seemed okay for a bit, but while it was loading it said that the C: was dirty and it had to repair. It did its thing and then booted back into Windows with no problem. 
Now, I would still like Ubuntu, but not at the cost of the computer. Should I retry the installer, (selecting the use largest amount of free space), or what? I am kind of freaking out here, so help would be greatly appreciated. :confused:
-Thanks!

---

### Post by Duck2006 on 2007-08-25
I would try Gparted live CD to partition the drive

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

defrage the drive twice or three times befor you try to partition the drive

---

### Post by Aiello on 2007-08-25
I don't want to seem arrogant, but I seriously need some help!!!
At this point should I just try to give all the HDD space back to Windows?! Or is there still a chance I can get 13gb of Ubuntu in a duel boot with out killing the computer?!

---

### Post by Aiello on 2007-08-25
Disregard my about post.

---

### Post by AceofSpades19 on 2007-08-25
first you have to make the windows parition smaller by 13 gb then you create a / parition for ubuntu taking up the remainder of the space and don't forget to defrag before doing this

---

### Post by Aiello on 2007-08-25
Erm... I can't defrag my Windows anymore. It doesn't have enough disk space.
And partitioning was the thing that got me INTO this problem. How can Gparted Live CD help get me out?

---

### Post by slimdog360 on 2007-08-25
You should perhaps read up a little more on partitioning. [http://www.psychocats.net/ubuntu/index.php]("http://www.psychocats.net/ubuntu/index.php") 

If you have the money and know how you could put an extra hard drive in your computer which makes things a little easier.

---

### Post by Aiello on 2007-08-25
Ok, apparently you guys don't know the situation. [http://ubuntuforums.org/showthread.php?t=534]("http://ubuntuforums.org/showthread.php?t=534")
That should help. Everything went "down the hole" after that.

---

### Post by Aiello on 2007-08-25
You guys post to fast. Okay.
I am kind of in a rut right now and basically I would like to get my HDD back to where it started. Can I just use Gparted in the Ubuntu LiveCD to increase my Windows partition back to where it was?

---

### Post by Aiello on 2007-08-25
Could I just increase my Windows partition (/dev/sda2) to accompany the unallocated part and everything would be fine? Windows would have full access to all the disk space?

---

### Post by AceofSpades19 on 2007-08-25
of course you can, if you delete the ubuntu parition

---

### Post by Aiello on 2007-08-25
So I just move the Windows partition over? I have a picture in my last post.

---

### Post by Lexi on 2007-08-25
What are you trying to do?  Create a partition for ubuntu or expand your Windows partition?

---

### Post by Aiello on 2007-08-25
Well, I tried to create a partition for Ubuntu, but it failed. Now I am trying to re expand Windows, so it has the full HDD.

---

### Post by Aiello on 2007-08-25
I am kind of in a hole here. Though I still might try Ubuntu in the future, I just REALLY want to get Windows back to having the whole HDD.

What Gparted looks like at this point:

---

### Post by Aiello on 2007-08-25
If I just do this will it be fine?

---

### Post by Duck2006 on 2007-08-25
Just use gparted to increse the size of your HDD

---

### Post by pgar23 on 2007-08-25
can you get on aim?

---

### Post by Aiello on 2007-08-25
Sorry I was a way for a bit. Thanks to all those who are helping me. This is kind of a Windows problem now, so I don't know if you guys will be able to help me, but here it is:
I used Gparted in the LiveCD to give all the disk space to the Windows partition. 
I then booted Windows and when to do a disk defrag to clean up the files, but then it says I only have 8% disk space or so and it can't defrag. Apparently Windows thinks Linux has the 30 some gigabytes, and Linux think that Windows does! So,in the command prompt typed:chkdsk
It then gave me this: The type of the file system is NTFS.

WARNING!  F parameter not specified.
Running CHKDSK in read-only mode.

CHKDSK is verifying files (stage 1 of 3)...
File verification completed.
CHKDSK is verifying indexes (stage 2 of 3)...
Index verification completed.
CHKDSK is recovering lost files.
CHKDSK is verifying security descriptors (stage 3 of 3)...
Security descriptor verification completed.
Correcting errors in the master file table's (MFT) BITMAP attribute.
CHKDSK discovered free space marked as allocated in the volume bitmap.
Windows found problems with the file system.
Run CHKDSK with the /F (fix) option to correct these.

  45761148 KB total disk space.
  41388728 KB in 99410 files.
     37280 KB in 8739 indexes.
         0 KB in bad sectors.
    658896 KB in use by the system.
     65536 KB occupied by the log file.
   3676244 KB available on disk.

      4096 bytes in each allocation unit.
  11440287 total allocation units on disk.
    919061 allocation units available on disk.

Any idea on what I should do? I know this is all in Windows right now and I completely understand if you guys can't help me, but I thought I would give it a shot.
-Thanks!

---

### Post by Aiello on 2007-08-26
I suppose that last post was out of desperation. Unless fixing this problem requires booting the LiveCD back up, I don't think I will be using Linux for a while. Thanks to all who have helped me on this trip into open-source, but I think I will be sticking with Windows for now.
...But still if you guys can help me it would be great!:lolflag:

---

### Post by AceofSpades19 on 2007-08-26
did you do what you did in post number 16?

---

### Post by Aiello on 2007-08-26
Erm... yes. That bad?

---

### Post by Aiello on 2007-08-26
Well, it is quite late on the Eastern Time Zone and I have been at my computer for about 6 straight hours with this whole fiasco. I need to wake up early to get some school work done too. Wont that be fun. I am logging off for now, but I will be back on tomorrow...erm... latter today (past midnight). 
In the mean time, keep those suggestions coming!
-Thanks

---

### Post by Aiello on 2007-08-26
I'm back. So the thing I did with Gparted in post #16 was bad?

---

### Post by Aiello on 2007-08-26
No responses... too bad I can't change the title of the thread. Some thing like OMFG 30GB OF MEH HARD-DRIVE GONE! might get more posts.

---

### Post by Aiello on 2007-08-26
Well, I guys since you guys wont help me, what are some good support sites for this issue?

---

### Post by bcarteruk on 2007-08-26
You could try what I have just done , give everything back to the Windows partition and then use the WUBI install of UBUNTU as that will install into a 4GB system and you can then grow the filesystem as needed within the Windows partition.

The penalty is a slighlty slower disk access , but you can always use LVPM to migrate it on to its own partitiion at a later date...

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by Aiello on 2007-08-26
The problem is I DID give all the disk space back to the Windows partition, or at least Linux thinks I did. After the installation didn't work out, I used Gparted to increase the Windows partition to the full HDD. But, Windows still thinks it is being limited. How can I get Windows to recognize the whole HDD?

---

### Post by Aiello on 2007-08-26
Any one? This is getting seriously frustrating. I can't save anything to my HDD! If you guys can't help me, could you at least point me to a site that could?

---

### Post by init1 on 2007-08-26
> **Aiello said:**
> Any one? This is getting seriously frustrating. I can't save anything to my HDD! If you guys can't help me, could you at least point me to a site that could?
All you have to do is resize you NTFS partition so that it fills the entire space. That should help.
Yes. That is exactly what you need to do. 
[http://ubuntuforums.org/showpost.php?p=3253963&postcount=16](http://ubuntuforums.org/showpost.php?p=3253963&postcount=16)

---

### Post by Aiello on 2007-08-26
I did that, but for some reason Windows will not recognize the part that was expanded to encompass what was supposed to be Ubuntu's partition.

---

### Post by init1 on 2007-08-26
> **Aiello said:**
> I did that, but for some reason Windows will not recognize the part that was expanded to encompass what was supposed to be Ubuntu's partition.
Weird. Give me a screen shot of Gparted.

---

### Post by Aiello on 2007-08-26
Here it is. Sorry about the delay. I was using Windows and it takes a while to boot into the LiveCD. 
And Windows should only be using about 50gb of space.

---

### Post by Aiello on 2007-08-26
I just noticed this. Gparted is saying that the partition has 70.93 gb used on it, but Windows is saying that it is only using about 48gb. What would be filling up that other 20 or so gb?

---

### Post by init1 on 2007-08-26
> **Aiello said:**
> Here it is. Sorry about the delay. I was using Windows and it takes a while to boot into the LiveCD. 
And Windows should only be using about 50gb of space.
Weird. I have a similar problem once. Do a chkdsk /f in windows if you can.

---

### Post by Aiello on 2007-08-26
I already did that. It told me it couldn't read part of the disk and if I would like to check that part on the next reboot. I exited, rebooted, and it did some disk checking. No difference though. 
Is this still a Linux problem or has it become a Windows problem?

---

### Post by Aiello on 2007-08-26
I guess I will do it again though. Give me a few minutes. I will post exactly what comes up in the command prompt.

---

### Post by Aiello on 2007-08-26
Here it is. 
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Eric Collins>chkdsk/f
The type of the file system is NTFS.
Cannot lock current drive.

Chkdsk cannot run because the volume is in use by another
process.  Would you like to schedule this volume to be
checked the next time the system restarts? (Y/N)

I typed "y" before and rebooted the system. All it does is check the disk and then go back into XP with no change.

---

### Post by Aiello on 2007-08-26
Any suggestions init1?
Or anyone for that matter?

---

### Post by Aiello on 2007-08-26
Oh, come on... Don't leave me stranded here!

---

### Post by eapache on 2007-08-27
XP has it's own partitioner that can only handle ntfs and fat. Go into Start>All Programs>Accessories>System Tools>Disk Manager (or something like that, I don't have it in front of me). Post a screenshot so we will see what windows thinks about your disk structure.

I believe the problem is something to do with the fat partition at the beginning of your disk. Many manufacturers put a recovery tool there or something, but they depend on the disk not being repartitioned. What brand is your PC (HP,Dell,etc.)?

---

### Post by bcarteruk on 2007-08-28
Chkdsk may not give you the space back - it will convert any orphaned chains into files - on my XP system these are hidden in the root directory of each drive as FOUND.nnn directories containing files FILEnnnn.CHK 

In windows explorer, Tools, Folder Options, View, click the Show hidden files and folders then go looking for the *.CHK files to go delete

---

