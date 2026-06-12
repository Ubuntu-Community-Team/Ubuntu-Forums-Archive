---
title: "Advice about reinstaling/repartitioning please?"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by tabithaboof on 2007-09-02
I am planning on repartitioning my HD and installing Xubuntu. I currently have an XP/Ubuntu dual boot set up with 

1 -  9 GB NTFS partition with XP installed

2 - 1 GB swap Partition

3 -  80 GB NTFS partition for shared data

4 - 6 GB ext3 partition with my Ubuntu partition

I would like to change this to 

1 - 5GB NTFS partition with XP installed

2 - Large FAT32 partition for misc data

3 - 5 GB ext3 Home Partition

4 - 5 GB ext3 Xubuntu Partition

5 - 1 GB Swap Partition

Basically a very similar set up to the one on Psychocats site here 

[http://img379.imageshack.us/my.php?image=partitioning4mz5.png](http://img379.imageshack.us/my.php?image=partitioning4mz5.png)

I have all my data backed up and I think these are the steps I need to follow

1 - defrag/cleanup windows

2 - Run Gparted from my Xubuntu live CD and delete all my partitions except the XP boot one

3 - Run Install from the Xubuntu live CD and partition the drive as above.


- I have just a couple of questions, how do I set a partition as /home?
- At which point should I resize my NTFS windows partition?

Main thing I guess, will the above acctually work as I think it will?

Thanks alot!

---

### Post by mikewhatever on 2007-09-02
> - I have just a couple of questions, how do I set a partition as /home?
- At which point should I resize my NTFS windows partition?

Main thing I guess, will the above acctually work as I think it will?


Resize the Windows partition before you go on creating all the new ones.
For every partition, a mount point must be designated, so home is mounted as /home. In a similar way, the storage partition can be mounted as /media/storage. 
There is no reason it should not work, but as always, there is a tiny chance it might not. Backing things up is a very good idea, therefor.
Good luck.

---

