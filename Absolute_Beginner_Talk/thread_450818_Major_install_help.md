---
title: "Major install help"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by baskettplayr on 2007-05-21
hi well ok i want to install linux on my computer so i decided i would use ubuntu, so i put on a cd and everything and it starts up and everything is fine until i get to the partitioning part.  (Background info: i want to dual-boot with my xp!) anyways at first i used a partitioning program acronis disk director and made a 32 gig partition thats was ntfs. and when i tried to install ubuntu on that partition it said something about a mount point... i didnt know how to fix that so i decided to join my 2 partitions together and just use that slider way of partitioning for ubuntu and then it said disk write error... the thing is i dont want to lose anything on my windows but i still want linux... if someone could help i would greatly appericate it. if anypart is confusing i will try to make it easier to understand...

---

### Post by smoker on 2007-05-21
you can make your partitions again with acronis disk director, and make 2 partitions for ubuntu, a 'root' partition, of at least about 5GB, and a 'swap' partition, around double the size of your ram (these are rough guidelines).

when you go to install, and you get to the ubuntu partitioner, select the 5GB (or whatever size) partition, and with the dropdown box, select the '/' without quotes, this will be your root partition. then select the partition for the swap, and with the dropdown menu select 'swap', then put a tick in the format boxes for only these two partitions, make sure your windows partition does not have a tick in the format box!

hope this helps and makes sense:-)

---

### Post by apostate on 2007-05-21
> **baskettplayr said:**
> hi well ok i want to install linux on my computer so i decided i would use ubuntu, so i put on a cd and everything and it starts up and everything is fine until i get to the partitioning part.  (Background info: i want to dual-boot with my xp!) anyways at first i used a partitioning program acronis disk director and made a 32 gig partition thats was ntfs. and when i tried to install ubuntu on that partition it said something about a mount point... i didnt know how to fix that so i decided to join my 2 partitions together and just use that slider way of partitioning for ubuntu and then it said disk write error... the thing is i dont want to lose anything on my windows but i still want linux... if someone could help i would greatly appericate it. if anypart is confusing i will try to make it easier to understand...

Hey there!

Maybe this will help.  Try to think of your linux filesystem as the internet. Every location is a URL. There are no drive letters, "C:" and there are no backslashes, only forward slashes.  The place called  /   ....is also called the filesystem "root".  Everything on your linux drive is under /.  It is like C:  \ in Windows.   So....your personal area, home, is   /home. There are other UNIX standard places that are right under root, and these places are called "mount points".  Every drive must be "mounted" i.e. mapped to a name.... /var, /etc, /opt are some you will see.  Don't worry about them too much, just think of it like this:

C:\Program Files  =  /usr

C:\Documents and Settings = /home

C:\Windows =  /root

...sort of.  Note that some of these folders will have partitions all to themselves, and some need not....each one isn't necessarily a drive, some are just folders, depending how you partition your set up.  So you need a / drive at the very least, and a swap partition that is twice this size of your RAM. 

Also, it looked like you were trying to put Linux on a NTFS filesystem, though I may have mis-read that.  If so, that won't work.  Linux must reside on an EXT2, EXT3 or RieserFS drive.  I suggest EXT3.

I hope that helps.

---

### Post by baskettplayr on 2007-05-21
yes thank both of you guys tons!!!!

---

