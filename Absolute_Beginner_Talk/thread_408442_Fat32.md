---
title: "Fat32"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by dmg025 on 2007-04-13
So I currently have a 250 gig hd with windows on it and a 180 gig with ubuntu.  all my music and videos are on windows.  I want to be able to share music among both hard drives.  Could I partition off a Fat32 drive on my 160 gig (ubuntu) and then some how access that with windows?  will i get both read and write capabilites on both OS's?  And Lastly, can i do this while logged into Ubuntu with Gparted or do i need to use the live disk (I don't want to lose data or have to reinstall so I am very hesitant to do this).  Thanks in advance

dmg025

---

### Post by Drithyin on 2007-04-13
I may be wrong, but I don't think GParted can change a partition it is currently running from. Thus, if you are shrinking the Ubuntu partition, I suggest the Live CD. 

As far as I know, Ubuntu and WinXP can both read and write FAT32, however, [this]("http://www.fs-driver.org/") installed on your windows system will let it read/write Ext2 and Ext3. So, you theoretically can share an Ext3 partition.

After rereading the post, I also want to stress that GParted should be able to shrink either partition without damaging the files. It can just chop off a chunk of free space, deallocate it, and then you can make it into whatever you want.

---

### Post by u04f061 on 2007-04-13
I agree with Drithyin.

---

### Post by Rotaj on 2007-04-13
I have a similar situation and Drithyin has the most straight forward answer. 
You might want to copy your music & videos from Ubuntu. It saves a few headaches regarding file permissions.

---

