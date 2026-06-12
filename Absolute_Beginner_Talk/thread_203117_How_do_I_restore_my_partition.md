---
title: "How do I restore my partition?"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by idontknow9999 on 2006-06-24
My Linux installed screwed up for the third time.

How do I restore all the partitions on my HDD's?

---

### Post by Apple 101 on 2006-06-24
What happened with your install?  A partitioning problem perhaps?

---

### Post by aysiu on 2006-06-24
You can't restore it unless there's something to restore.

[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by idontknow9999 on 2006-06-24
> root (hd2,1)
Error 22: No such partition.

But I do not want to try to fix it... Because I told it 2 install on the wrong HD :( :( :(

So I want to remove that partition on THAT HDD, and I want to remove the other partition on my main HDD (the originally linux f up).... That way I could re-try from scratch on the right HDD....

---

### Post by idontknow9999 on 2006-06-24
[QUOTE=aysiu]You can't restore it unless there's something to restore.

[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)[/QUOTE]

I just want my partition back to 100% normal....

---

### Post by Apple 101 on 2006-06-24
Was there anything important on that partition (the one you didn't want to install Ubuntu to)?

---

### Post by idontknow9999 on 2006-06-24
[QUOTE=Apple 101]Was there anything important on that partition (the one you didn't want to install Ubuntu to)?[/QUOTE]

I only "extended" that partition.... It is my High Definition movie HDD....

Problem is, total size for that HDD is now 58 GB... It should be 160GB...

Then, on my main HDD, its 200GB, but I originally gave it 100 GB for windows xp and 100GB for Linux.

---

### Post by catlett on 2006-06-24
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) Download and burn this iso to disk. Boot to the disk. It will boot into gparted which is a partitioning application.

Delete any partitions you do not want. Then resize your remaining partition so it is the entire disk. This will leave you with one partition.

If you want more than one partition, this application can do anything. Start by deleting the ones you don't want and then either resize existing partitions or create new ones.

---

### Post by Drakkor on 2006-06-24
Nevermind,lol

---

