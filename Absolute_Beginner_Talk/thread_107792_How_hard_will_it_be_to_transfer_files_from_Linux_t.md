---
title: "How hard will it be to transfer files from Linux to Windows"
date: 2005-12-24
forum: Absolute Beginner Talk
---

### Post by dueY on 2005-12-24
By from Linux to Windows I mean from ext2 or ext3 to FAT or NTFS.

From what I understand Linux and Windows can both r/w/e to FAT partitioned drives.  Right now I have an 80Gb HDD with a ~50/30 GB NTFS/ext3 split.  My NTFS partition is about 94% full and my ext3 drive is about 30% full.  I'm getting a 250GB HDD for Christmas.

I'm wondering how hard it will be to get the files I'm downloading with Ubuntu now onto my new harddrive/possibly onto a NTFS partitioned drive in the future.    

I think I'll set aside atleast 100GB on my new drive as FAT for sharing with Windows and Linux.  This won't be a problem, will it?  They will play nice together, right?

---

### Post by fordfan753 on 2005-12-24
Having a shared FAT32 partition is a great idea, I have one on my computer.

As far as transferring from linux to windows, keep in mind that linux **can not** write to NTFS

---

### Post by dueY on 2005-12-24
[QUOTE=fordfan753]Having a shared FAT32 partition is a great idea, I have one on my computer.

As far as transferring from linux to windows, keep in mind that linux **can not** write to NTFS[/QUOTE]

I know, that's why part of the drive will be FAT despite Windows XP still being my "main" OS (maybe this will change once I get games running on my Ubuntu :D  ).  

So there won't be any shenanigans getting my data to the new harddrive?  Can I just copy&paste or drag the files from ext3 to FAT32?  Then will it be ok to bring those files from FAT32 to NTFS in the future if I want?

---

### Post by MetalMusicAddict on 2005-12-24
[THIS]("http://www.ubuntuforums.org/showthread.php?t=107311") threads gets a little silly but you might find it usefull.

---

### Post by dueY on 2005-12-24
[QUOTE=MetalMusicAddict][THIS]("http://www.ubuntuforums.org/showthread.php?t=107311") threads gets a little silly but you might find it usefull.[/QUOTE]

Interesting thread, I may try that in the future but for now I think I will just set up a FAT32 partition.  

And my original questions still stand: Can I just copy&paste the files from my ext3 partition to the FAT32 partition without any weird terminal commands or anything else?  And will those same files now on the FAT32 partition be able to be copied and pasted to a NTFS partition at a later date if need be?

---

### Post by MetalMusicAddict on 2005-12-24
[QUOTE=dueY]
And my original questions still stand: Can I just copy&paste the files from my ext3 partition to the FAT32 partition without any weird terminal commands or anything else?[/QUOTE]
Yes. As long as your permissions are set right.
> And will those same files now on the FAT32 partition be able to be copied and pasted to a NTFS partition at a later date if need be?
Yes. As long as your permissions are set right. ;)

---

### Post by dueY on 2005-12-24
[QUOTE=MetalMusicAddict]Yes. As long as your permissions are set right.

Yes. As long as your permissions are set right. ;)[/QUOTE]

Cool.  Thanks for the replies and the link to the other thread.

---

