---
title: "percentage for each partition"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2006-06-02
I am going to try to install the Dapper Drake release version on a couple of different systems this weekend.  One has an 18gb SCSI drive and the other has an 80gb SATA drive.

When I installed the beta version before on one of the systems, I only made two partitions, 1 for the FS and 1 for SWAP.

But when you make only these two partitions as above, apparently a /home directory is automatically created.  How does the hard drive spacing for the root file system and the /home directory work, in that case.  Is the space that is allocated to each a fixed amount or is it dynamic ?

In any case, if I create three (3) partitions on the new installs (1 for FS, 1 for home, 3 for SWAP), what percentage of the drive should I allocate to each ?  And particularly what amount of space should the allocated to the O/S including future updates, etc ?

Thanks.

---

### Post by catlett on 2006-06-02
/ (root) 5gb
swap 512mb
/home whatever is leftgb

root holds the base install and any applications you add. I don't think anyones gone over 5gbg. I'm at 3.5gb with three window managers installed i.e. gnome,kde,xfce.
swap is "hard disk ram" just like windows swap file. The rule of thumb is twice your ram i.e. 256mb=512swap.Most people don't touch their swap unless they do video editing or ram intensive stuff. Home holds all your documents,mp3s,videos etc. So that should have the most space. The good thing about a seperate home is that if you need to reinstall or upgrade the installer will leave your home alone and only format your root partition. Thus updating your system without touching your personal data

P.S. If you have plenty of space you can go up on the root just to be safe. Personally even though 5gb is plenty mine is at 7.5gb. I have a 100gb and a 60gb external so I figured , why not have plenty.

---

### Post by bluefrog on 2006-06-02
if not specified otherwise, /home is part of /.

size of your partitions depends on what you want to do. if you want to create dvd from your home videos for example then you will need at a point something like 9 free GB in /tmp. If you only make 3 partitions /tmp will be part of / so size your / accordingly.

So let's say 20 gig for / , twice your ram for swap and the rest for /home. Some will say it's way oversized for / , well I don't care with the large drives we have now...
Just make them big and your mind is free for quite a long time afterwards.

James

---

### Post by aysiu on 2006-06-02
You might want to read this:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by wpshooter on 2006-06-02
Thanks for your replies.

---

