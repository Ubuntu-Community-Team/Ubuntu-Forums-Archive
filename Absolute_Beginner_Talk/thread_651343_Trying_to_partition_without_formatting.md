---
title: "Trying to partition without formatting"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Sveninarxao on 2007-12-27
I installed Linux two days ago with little to no direction. I began with 2 hardrives on my system: one 160gb from Windows and a 5.5gb backup(it came included on the computer in case windows failed). I decided to format the 5.5gb backup into a 5gb root and .5gb swap. This worked really well, but now I realize that I love Linux and want the 160gb as my root.

I realized that the solution to this problem then is by changing the partition from ntfs(?) to a root with  gparted. The only problem is that I have sensitive material on the 160gb hdd like my 10gb music collection. Now, I was wondering if it is possible to resize or change this partition without formatting the harddrive, therefore sparing my files. I would like to maintain a small part of my Windows hard drive in case I ever have to use it for some reason. 

Is this possible?

If not, should I just steal my dad's external hard drive, put my music and docs on it, and format the 160gb?

Sorry, if my explanation doesn't make much sense. If you need any further info to help, just ask.

---

### Post by mellowd on 2007-12-27
The 5.5gb is probably not even a hard drive, more than likely just a portion of the 1 hard drive dedicated to restoring

---

### Post by Sveninarxao on 2007-12-27
If it helps also, the 160gb windows portion is flagged as a boot in gparted.

---

### Post by reality_hunter on 2007-12-27
hi Sveninarxao,
when you use"gparted-live cd" and load to gnome, you can select the 160 GiB hard disk from the top right of the window that is first opened.  After that you can select to resize and move the ntfs/windows partition to the right and with as mush space as you would like to assign to that partition.  The unallocated partition thats on the left bar now..you can click new and make it ext3 and mount point "/"
try this, but again you should still remember to backup when doing something like that just in case ...so I would suggest to steal/borrow that external HD for few hours, as moving the data will within a partition will take couple of hours. Hope this helps:)

---

### Post by p_quarles on 2007-12-27
Which version of Windows are you using? If it's Vista, you should note that Gparted does not get along very well with that. It's much safer to use Vista's own partition editor to shrink the main partition.

And, like reality_hunter said, you should not attempt to edit your partitions using any tool until you have backed up all sensitive data from that drive. Chances are, you won't lose anything, but that's no excuse to run the risk.

---

### Post by Sveninarxao on 2007-12-28
Thank you very much for the explanation. I'm currently trying to dig up a blank cd-r to burn gparted on. 

The only thing which I cannot understand in your description is turning the "to-be-created" ext3 partion into a "/" or root. Won't this override the / drive(only 4gb) that I already have?

---

### Post by dstew on 2007-12-28
Actually, you can format a partition without specifying a mount point. You can then mount the partition as you wish. However, if you are installing a *new* system, you have to specify a root mount point for at least one partition. There is a way to set a new root mount point in an old installation too, but I don't know much about that.

---

