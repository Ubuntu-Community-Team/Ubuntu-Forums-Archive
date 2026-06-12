---
title: "[SOLVED] Cannot allocate free disk space to Windows partition with GParted"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by eamann on 2007-12-04
Hello!

I know that similar questions have been asked before, but the previous situations do not correspond to my problem.

I have just installed Ubuntu 7.10 on a Dell Inspiron 1520, keeping XP. The partitioning process has turned out to be more complicated than I thought and I need advice to configure the partition structure properly.
 
I have ended up giving insufficient space to my Windows partition (Sda2 NFTS).

Therefore I sliced off 15 Go from Sda 6 (Ext 3) which is where Linux is installed. The unallocated space is between the Windows partition and the Linux partition.

However, I cannot get Gparted to allocate the resulting free 15 Go to the Windows partition, even when it is unmounted and when I use the live CD.

Thanks in advance for your help!

---

### Post by overdrank on 2007-12-04
> **eamann said:**
> Hello!

I know that similar questions have been asked before, but the previous situations do not correspond to my problem.

I have just installed Ubuntu 7.10 on a Dell Inspiron 1520, keeping XP. The partitioning process has turned out to be more complicated than I thought and I need advice to configure the partition structure properly.
 
I have ended up giving insufficient space to my Windows partition (Sda2 NFTS).

Therefore I sliced off 15 Go from Sda 6 (Ext 3) which is where Linux is installed. The unallocated space is between the Windows partition and the Linux partition.

However, I cannot get Gparted to allocate the resulting free 15 Go to the Windows partition, even when it is unmounted and when I use the live CD.

Thanks in advance for your help!
HI and first thing that comes to mind is that if you have a window, ubuntu, swap and hope partition then yes gparted will not allow you to manipulate the partition because you are limited to four partitions to a drive unless you create a extended partition. Could you post a screen shot of the gparted window?

---

### Post by eamann on 2007-12-05
Thanks for reacting!

In the end I had to do another install and I was able then to increase the size of the Windows partition.

Thanks again!

---

