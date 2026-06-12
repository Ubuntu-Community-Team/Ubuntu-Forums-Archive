---
title: "Looking for a specific tutorial... (Installation and partitioning)"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by CopiousX on 2007-02-07
All of the tutorials I'm finding for Ubuntu only deal with installing Ubuntu on a new hard drive. I'm interested in installing Ubuntu on an existing, unused D: drive partition, seperate from the C: partition on the same hard drive. I don't want to screw up the C: partition because it has EVERYTHING on my compy, so I'm looking for a tutorial that deals specifically with installing Ubuntu onto an existing partition.

---

### Post by Darklighter137 on 2007-02-07
What exactly is on that partition?  Are those two your only partitions?  If so, use the Ubuntu installer to delete the partition you don't want, and then go back to the initial partitioning step and tell Ubuntu to use the largest amount of free space it can find.  I just did the same thing and it worked out really well.

Now, even with something as simple as deleting a partition, there is always a very small possiblity of data corruption on the other partition, so you should take the time to back up your important files (you should do this often in case of disk faliure anyway).  Happy Ubunting! ^_^

---

### Post by raul_ on 2007-02-07
A different hard drive or a different partition? those are 2 different things. Anyway, to me it looks just like a dual boot setup. How could you miss the guides? :D 

here:

[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

But be careful: I'm not sure how to proceed to install on a different HARD DRIVE. So you may want to search a little more about that. It shouldn't be different, i think you'll just have to tweak the loader :)

But again, i'm 100% sure this guide has been done before (whatever your case is)

---

### Post by Bartender on 2007-02-07
Here are 2 extensive threads...

[http://www.ubuntuforums.org/showthread.php?t=271968](http://www.ubuntuforums.org/showthread.php?t=271968)

[http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by Sef on 2007-02-07
Also read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/") for installing from the alternate cd.

[Psychocat's]("http://www.psychocats.net/ubuntu/installing") is for installing from the Live CD.

**Back up** your data first.  Nothing is guaranteed 100% to work perfectly.

---

### Post by CopiousX on 2007-02-09
I'm looking to install on the same hardrive as what Windows is on. I'm just trying to be careful and avoid deleting the Windows partition. One question that I have is, willl setting the Windows partition as the swap erase it?

---

### Post by Zuuswa on 2007-02-09
using the Windows partition as swap will format and delete it . . . you should just make another partition for the swap file, as it uses a differant filesystem

---

