---
title: "Dual Boot with my specific setup and introduction!"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by choppra on 2007-06-21
Hey guys,
I'm new to the Ubuntu community.  All i have to say is WOW.  I consider myself an Windows Expert.  My current job is Level 2 support for a large financial firm.  I really HATE windows.  I work with it all day and I've just learned to hate it.  Anyway, I really don't know much about Linux and after using Ubuntu for a few weeks now on a laptop, I've fallen in love.  I would like to setup a dual boot on my home machine but am concerned with how to actually do it on my setup.

Heres the situation...

Internal Drive 300 GB.
50GB Allocated to Windows (I have alot of things installed)
250 Partition used for MyDocuments. (use about 140 so far)

I would like to do the following.

Setup Dual boot with Ubuntu and Windows XP but still have the partition available on both operating systems.  Is that Possible?  What steps would I have to go through to make this happen?  Which do I still first?  Also, can anyone recommend a beginners book for trouble shooting Linux?  Thanks!!

---

### Post by stevebakerj on 2007-06-21
Free online books here:

[http://vntutor.blogspot.com/2007/06/free-online-ubuntu-linux-books.html](http://vntutor.blogspot.com/2007/06/free-online-ubuntu-linux-books.html)

---

### Post by steve-shinn on 2007-06-21
Try this link also ....

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

---

### Post by choppra on 2007-06-21
Cool, thanks guys!  Any help with my current setup?

---

### Post by stevebakerj on 2007-06-21
For Dual boot:

[http://book.opensourceproject.org.cn/distrib/ubuntu/hacks/](http://book.opensourceproject.org.cn/distrib/ubuntu/hacks/)

Hack #6

---

### Post by choppra on 2007-06-21
Hmm, i see the dual booting but what about my situation with the secondary partition that has all my files?

---

### Post by stevebakerj on 2007-06-21
**[COLOR="Red"]NB    Backup, backup and then backup again[/COLOR]**

I would go back to XP and defrag your data partition a couple of times, then use the 'Disk Management' Tools in XP to 'shrink' it down to 200Gig say, leaving 50 Gig for Ubuntu.

Then boot from the Live CD and click install, select your own language, time zone and country settings then when you get to disk setup, choose 'guided' use the largest free space, this should be the 50Gig you have just unallocated in XP. Then continue with your own preferences.

---

### Post by stevebakerj on 2007-06-21
Then when you have successfully got your Dual Boot setup you might want to read and write to your NTFS partitions, to do that read here:

[http://ubuntuforums.org/showthread.php?t=217009&highlight=Read%2FWrite+NTFS](http://ubuntuforums.org/showthread.php?t=217009&highlight=Read%2FWrite+NTFS)

---

### Post by choppra on 2007-06-21
what if I convert my Data Partition to FAT32.  After installing Ubuntu how do I make it so that /home points to that?  Can that be changed after install?

---

### Post by p_quarles on 2007-06-21
Ubuntu will automatically mount all primary partitions on the drive it's installed to. You can't put your Ubuntu /home folder there, though, because that needs to ext2/3 filesystem. I wouldn't do the FAT32 format, if it's already NTFS. It will be a lot less work just to install the program that allows Ubuntu to read NTFS. 

Just remember to defrag the volume you're shrinking (twice, to be safe) and BACK UP you're data. (do a quick search on the forums for "what happened to my Windows?" for why). Partitioning a non-empty drive can be risky.

---

