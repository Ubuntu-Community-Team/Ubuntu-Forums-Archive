---
title: "Drive re-sizing/partioning"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by RamR on 2008-03-30
When I installed 7.10 a week ago it was to have a look around the OS to see if I liked it.  Well, I've done a lot in a week and really do like it.  One of the problems I now have is that I went for the simple dual boot setup that basically split my 40GB drive in half, one for XP and one for 7.10.  I did this even though I was aware that there were much better HDD partitioning strategies out there. 

So, now I have two questions. 

1. Which is considered the best setup of partitions?

2. Can I repartition my drives without having to re-install either OS or lose all the setup I have done in Ubuntu over the past week?

Thanks for any help.

---

### Post by Moop on 2008-03-30
There really isn't a best setup for partitions. It's whatever works best for you. I prefer using a separate /home partition because it makes it easy to save settings and data when reinstalling etc. 

You can resize your partitions without losing any settings or data by using a GParted live cd or similar. You could also shrink a partition and use the free space to create a new partition. Doing any of those will change the partitions uuid and cause boot problems so you will want to check out how to change or eliminate the uuid in grub. 

Sometimes it's just easier to start over with the partition setup you want.

---

### Post by Daveth on 2008-03-30
I'm pleased you have decided to install- you will have fun.
This is a reasonable guide for partitioning

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

this a nice pictorial guide for using gparted to achieve partitions from your live cd

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

or this

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Remember to fully defrag your windows before you start playing with partitions, and do back stuff up. I would go for a separate /home partition as well, you you can move easily from gutsy to hardy with interfering with your personal data. This is a good home guide

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by housam on 2008-03-30
download and burn the newer version of Gparted and boot from it'll allow you to resize and create partitions easily - I mean the mounted ubuntu partition can not be resized from the live cd.

---

### Post by RamR on 2008-03-31
> **Moop said:**
> There really isn't a best setup for partitions. It's whatever works best for you. I prefer using a separate /home partition because it makes it easy to save settings and data when reinstalling etc. 

You can resize your partitions without losing any settings or data by using a GParted live cd or similar. You could also shrink a partition and use the free space to create a new partition. Doing any of those will change the partitions uuid and cause boot problems so you will want to check out how to change or eliminate the uuid in grub. 

Sometimes it's just easier to start over with the partition setup you want.

Ok, I've looked at the link here [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) which describes the different partition options.  I like the one which has a 5 partitions; Windows (NTFS), Shared Data (Fat32), Ubuntu /home (Ext3), Ubuntu / (Ext3), and Swap.

I am however a bit worried about the above warning that changing the partitions also changes the partition uuid (not sure what that is) and cause boot problems.  Is there any problems with eliminating the uuid in grub?  How do you go about this?  Does this result in a system that is equally stable to one where the partitions are made before installing Ubuntu?

Lots of questions I know but I have one more.  I have a 40GB drive on my laptop and if I am going with the afore mentioned partition plan what would be the best sizes for each partition?

Thanks for so many quick replies... this support alone is enough of an advantage to change from windows.

---

### Post by abhilashkumar on 2008-03-31
**Back up your data!**

I have 2 Partitions for Windows (50 GB System and 100 GB store)
2 partitions for Ubuntu (10 GB for everything and 2 GB for SWAP)

---

### Post by RamR on 2008-04-06
Finally got around to trying this.

Created a Gparted LiveCD but when I try to boot from it it takes me to a Grub Command line.  It doesn't seem to work or I don't know what to enter at this command line.  Any suggestions?

---

### Post by confused57 on 2008-04-06
> **RamR said:**
> Finally got around to trying this.

Created a Gparted LiveCD but when I try to boot from it it takes me to a Grub Command line.  It doesn't seem to work or I don't know what to enter at this command line.  Any suggestions?
When you first boot the Gparted Live CD, you could try selecting "vesa" graphics.  Also, if you read the message just above the Gparted root prompt, there is a command listed you can enter to manually set your video "driver" and desired resolution.  You can check your video driver in your Ubuntu install:
```
gedit /etc/X11/xorg.conf
```

---

### Post by RamR on 2008-04-06
I still can't get the Gparted LiveCD to boot.  

Is it possible to shrink the Windows partition down to the minimum possible size while Ubuntu is mounted? Then using the space saved here to create a ubuntu /home partition?  

I've decided to go for a Windows, ubuntu /home, ubuntu/ , swap setup.

---

### Post by RamR on 2008-04-06
OK, figured this out myself... needed to install ntfsprogs.

Now I have a resized windows partition and an new ext3 partition.  How do I make this new partition the ubuntu /home partition?

---

