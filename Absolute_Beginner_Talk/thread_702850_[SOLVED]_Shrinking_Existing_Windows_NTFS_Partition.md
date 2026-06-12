---
title: "[SOLVED] Shrinking Existing Windows NTFS Partition Advice Needed"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by alever on 2008-02-20
I have a 120 gig hard drive and the entire drive is formatted NTFS for Windows XP.  I have about 90 gigs free. I want to try out Ubuntu and have the 7.10 install disk.  From what I have read, the Ubuntu installation program is supposed to give you the option to resize your existing partition, but I never got that option when trying to install.  I tried defragging, still didnt get the option.

It seems like my best bet is going to be to resize it using some other tool.  I have read a lot of nightmare stories about resizing a Windows partition and then having Windows freak out etc.  I would really like to avoid that hassle.

I have a couple of questions and welcome any additional advice you would like to give.

1. How risky is it to resize an existing partition?
2. Is it better to use qtparted via the Recovery CD referenced in some of the Ubuntu documentation or some other program like Partition Magic?

---

### Post by jan quark on 2008-02-20
Make a backup of your important data now

before even thinking of partitioning

after said this, I would not use partition magic, because I have heard to many complaints after using this application

use the gparted live cd instead

shrink your windows partitions but defragment the windows partition first, because windows has the habit to store files everywhere on the partition and when you shrink an unorganized widows partition files my get trunkated 

gparted is a powerful tool and it will do what you says to it

---

### Post by Shazaam on 2008-02-20
1. If done correctly you will be fine.
2. IMHO the best partitioning tool is the gparted livecd.....
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

Before you resize, DEFRAG  Windows. This is a MUST DO. Then use either the Ubuntu livecd or the gparted livecd to do your partitioning.

---

### Post by herbster on 2008-02-20
Would the defrag need to be done from within Windows with its defrag tool ?

---

### Post by Duck2006 on 2008-02-20
> **herbster said:**
> Would the defrag need to be done from within Windows with its defrag tool ?

Yes it should be done from within windoze.

---

### Post by alever on 2008-02-20
Should I be worried at all by the fact that the ubuntu live installation cd wont do the resize as part of the installation process?  Maybe when windows defragged it left data all over the partition?

---

### Post by bodhi.zazen on 2008-02-20
> **alever said:**
> Should I be worried at all by the fact that the ubuntu live installation cd wont do the resize as part of the installation process?  Maybe when windows defragged it left data all over the partition?

Worried is an overstatement.

Boot to windows and try to defragment again. If that does not fix the problem, are you running XP or Vista ?

To all: Just a FYI, The Ubuntu desktop CD, as of 7.10, has gparted so there is no need to download the GParted live CD. In addition, the Gparted Live project has forked.

With that said, I too like the Gparted Live CD, it is a handy tool.

---

### Post by alever on 2008-02-22
I am running XP.  I ran defrag again.  It looks like the defrag tool keeps putting a small amount of data at the very end of the partition.  I think that may be what is causing the problem.

---

### Post by dstew on 2008-02-22
The immovable data is probably a Windows page file, sort of like swap in linux. It is used for virtual memory. You need to turn off paging first, then defragement. I think that you use the Memory control panel. In Virtual Memory settings, there is something like "Use Paging" or pagefile. Disable that (no page file). After that, if you want to free up space, you can find the page file (pagefile.sys) and delete it. But, I think that once you turn off paging, reboot, and defragment you will be all right.

---

### Post by alever on 2008-02-24
Thank you everyone for your help.  Removing the paging file worked like a charm.

---

