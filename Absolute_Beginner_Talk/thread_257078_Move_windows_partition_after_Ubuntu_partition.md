---
title: "Move windows partition after Ubuntu partition"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by rdilliker on 2006-09-14
Hi,

I've tried searches in several different ways but haven't quite found the answer to my questions.

I have 1 hard drive with 2 NTFS partitions that occupy my entire hard drive, WinXP installed on one of them. I read on Herman's site it is better to install the Ubuntu partition in front of the NTFS ones since ext3 partitions can't be resized from the front. I'm trying to find out how I can safely resize my NTFS partitions and move them to the end of my drive.

I have the gparted liveCD and I went ahead and resized my 2 NTFS partitions. This ended up leaving a gap of unformatted space after my 1st and 2nd partitions. This also ended up changing the drive letter of my 2nd partition from D: to E:. So I basically have 2 questions.

1) How do I correctly resize and move my NTFS partitions to the end of my drive so I can create my ext3 partitions at the beginning?

2) How is windows able to boot correctly if I move my boot NTFS partition since I'd think the MBR would be pointing to the wrong place now that my partition has moved?

Thanks for any replies.

---

### Post by bodhi.zazen on 2006-09-14
As to the first question I am not sure as I have never done this. My understanding is you would move your partitions. ie move the second ntfs partition to the space adjacent to the first partition. I do not know if you can do this in 1 or 2 steps. Perhaps there is documentation on the GParted site?

As to the second question, you would need to re-configure your boot program. I am not familiar with how to configure windows, but ubuntu will install grub which will be able to boot your windows partition.

Keep in mind[list=number][*]Windows needs to be on a primary partition.
[*]Moving and resizing partitions has the risk of data loss. Back up your data if you have not done so already.[/list]

---

### Post by subzero79 on 2006-09-14
This is and idea....back up your important data first. Try using ntfsclone that is intended for making exact images of ntfs partitons. you can them restore them to remain exact the same. Maybe try making at the end of the drive a a partition to put the image backup files of xp and your second partition and then try resizing and installing ubuntu.

---

### Post by rdilliker on 2006-09-14
Well I am working on a solution and I might be able to figure it out. I am pretty sure I saw on Herman's page or some other page linked from there how to do this but now I can't seem to find the page. Anywyas, I have to keep my partition numbers the same so I have to move my windows partition to another temp partition and then delete the original windows partition. Then I can create a new windows partition with the same partition number as the original one and can copy the temp partition here. 

I've taken care of backups, I use Acronis True Image to image to an external drive so I'm not concerned with data loss.

A question I do have is how does the filesystem locate files when I  move a partition? Doesn't the filesystem store the physical location on the hard drive somewhere, like what sector a file is located in? 

Also, once I move my windows partition, I think I'll have to run fixmbr from the WinXP CD to correct the MBR to point to my moved windows boot partition even though it kept the same partition number. I'm going to try this out, but is this correct?

Thanks.

---

### Post by bodhi.zazen on 2006-09-14
This is a very new feature in GParted.

Try the Gparted forums:

[GParted Forums](http://gparted-forum.surf4.info/)

Or documentation:

[GParted Documentation](http://gparted.sourceforge.net/documentation.php)


OOps, wrong thread.

What the heck, it might help this one as well.....

---

### Post by rdilliker on 2006-09-14
Well, I successfully moved my partitions to the end of my drive. I didn't even have to run fixmbr so I'm a little confused. 

1)How was the BIOS able to find NTLDR since it moved its physical location on the drive without me fixing the MBR?

2) How is it possible to move partitions around and the filesystem can still locate which sector a file is in? Is there some sort of table that GParted fixes when I choose to "move" a partition?

Thanks, I'm curious!

---

### Post by bodhi.zazen on 2006-09-14
Post a how-to.

---

### Post by rdilliker on 2006-09-14
> **rdilliker said:**
> Well, I successfully moved my partitions to the end of my drive. I didn't even have to run fixmbr so I'm a little confused. 

1)How was the BIOS able to find NTLDR since it moved its physical location on the drive without me fixing the MBR?

2) How is it possible to move partitions around and the filesystem can still locate which sector a file is in? Is there some sort of table that GParted fixes when I choose to "move" a partition?

Thanks, I'm curious!

Ok, I read more about NTFS and think I have the answers to my own questions.

1) The partition table was updated to reflect where my boot partition with Windows was moved so the BIOS jumps to the boot sector on this partition. The boot sector is where the code to call NTLDR is.

2) For NTFS I guess Gparted modified the master file table which is located after the boot sector on the partition. The master file table is where information on the physical location of files is maintained.

HTH.

---

