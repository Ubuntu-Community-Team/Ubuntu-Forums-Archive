---
title: "Partitioning Help  (I'm currently installing on my other computer)"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by Paul133 on 2006-08-24
I've started to install Ubuntu from the alternate CD and I've gotten to the partitioning phase I started with 36.8 GB NTFS, and 16.4 MB Fat16, and 3.2 GB Fat32, and roughly 8GB of free space. I've currently made it a little over 6 GB of ext3, 30 GB NTFS, 3.2 GB Fat32, and 16.4 MB of Fat16. I've now clicked write to disk but I'm told there's a bug in my Fat16 partiiton, something about Windows not liking the numbers of files in the partiitons. This seems harmless, but I'm not sure...:confused: I don't want to kill Windows :frown: (at least not until I know I love Ubuntu! :-D ) Any help is greatly appreciated!

---

### Post by TrendyDark on 2006-08-24
I think the FAT16 maybe too small, although, you never mentioned having a Swap partition, Ubuntu needs one that is about 2x the size of your RAM.

---

### Post by Paul133 on 2006-08-24
I do need to put in a 512 MB swap as well. And so, what do you think I should do with the Fat16? Was it a mistake to resize the NTFS partition with the text installer?

---

### Post by seshomaru samma on 2006-08-25
Paul133
Can you give more information about your partitions?
Do you have Windows on the NTFS partition?
What do you have on the FAT32 and FAT16 partitions?
Can you move your files from the FAT16 to another partition and then format it? This will be the easiest way...

The ideal dual boot would be :
Windows on NTFS
Shared files on FAT32 (or Ext3)
Linux on Ext3
Swap

---

### Post by distroman on 2006-08-25
First of, if you got windows installed on the NTFS partition, you don't want to mess with that partition in any way. I am pretty sure you what to leave it alone. 

Second, I can't think of anything you can do with FAT16, so unless you know, don't create any FAT16 partitions. 

It sounds to me like you are trying to get dual boot. Install windows first, sounds like you already have. You can prepare your linux partitions before you install ubuntu, if that's easier. 

I would advise you to make 3 partitions
/(root)
/swap
/home
/FAT32 – if you want to share files between windows and ubuntu. 

But please take a look at some guides and if you need more info there's lots to be found. 
There's also lot's of ways to do an dual boot install. So think about your needs.
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

---

