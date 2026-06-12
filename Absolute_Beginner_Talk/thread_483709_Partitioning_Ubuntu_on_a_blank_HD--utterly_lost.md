---
title: "Partitioning Ubuntu on a blank HD--utterly lost"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by hul on 2007-06-25
I'm trying to install Ubuntu FF 7.04 on a 500 GB hard drive from the LiveCD.  I want to install Ubuntu on a 100GB partition, not the full thing.  From all the help files I've read, this should be easy.  It is not.

For one, when I go to the installation and select "Guided Partition", no slider shows up that would allow me to pick the size of the partition I want Ubuntu on.  It only allows for the entire hard disk to be devoted to Ubuntu.  One help file said this was an indicator something is wrong with my hard disk.  The thing is only a month old!  Previously Windows XP was installed--before I deleted it everything worked fine.  What could be wrong, and how would I know?

I could try partitioning using the manual option, but here I'm really lost.  What's a partition table?  OK, I hit "new partition"--what's a mount point?  The installer won't let me proceed without specifying one.  Again, I search for help through Google and the forums and everything seems to demand a higher technical knowledge than I currently possess.  I did find something about creating a home partition.  Is this separate from the Ubuntu partition?  Is this on a different mount point?

I feel dumb--I knew my way around Windows pretty well, or at least better than most.  If someone could help me figure out what to do--or at least point me to a FAQ on partitioning aimed at those with very little technical knowledge of the subject it would be greatly appreciated.

Thank you!

---

### Post by kspn on 2007-06-25
You can do the Manual Partition option, you just need to make sure it is setup correctly.

The parts that you may get stuck on are:
Mount Point for first partition: **/**
Format for the first Partition: **ext3**
You will also need a swap partition, create a second _New Partition_ and select the format as **Swap**

Hope this Helps.

---

### Post by mikewhatever on 2007-06-25
Try using the following guide [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

---

### Post by southernman on 2007-06-25
Instead of using guided, do the manual option. Set your drive up this way (IMO):

swap (twice the amount of ram you have)
/ (20 gb - format as ext3 and make it bootable)
/home (as big as you like - format as ext3)

Setting up a seperate /home partition, will ease your troubles for future upgrades... or in the rare event you would need to completely reinstall Ubuntu. Do yourself this favor.

HTH's

---

