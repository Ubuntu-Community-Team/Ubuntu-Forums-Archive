---
title: "Partitioning hard drive prior to install"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by HenBar on 2007-07-13
I am about to install ubuntu on an older machine which now has Win98SE.  I have made a full backup of the entire system and I do not need any files on this machine so I can repartition and reformat the entire 40GB hard drive (it presently has 4 Fat32 partitions)  I would appreciate advice on the best procedures to follow before or during the installation so far as number and size of partitions to be created and how to do this.  I have the ubuntu install cd burned and ready to go (I have booted from the cd and the machine seems to like it fine)

Any thoughts/suggestions greatly appreciated.

---

### Post by hackle577 on 2007-07-13
I would go for 7-8 GB for root and the rest for /home (minus 1 GB at the end for swap).

You also might want to read [this]("http://www.psychocats.net/ubuntu/partitioning"). You won't want any of the dual boot schemes though.

---

### Post by ReaderRat on 2007-07-13
If you are not familiar with partitioning, you might peruse this:[Partitioning Basics](http://ubuntuforums.org/showthread.php?&t=282018)

---

### Post by wildseven on 2007-07-13
A good rule of thumb is to make the Swap partition equal to the amount of ram.

---

### Post by candtalan on 2007-07-13
> **HenBar said:**
> I am about to install ubuntu on an older machine which now has Win98SE.  I have made a full backup of the entire system and I do not need any files on this machine so I can repartition and reformat the entire 40GB hard drive (it presently has 4 Fat32 partitions)  I would appreciate advice on the best procedures to follow before or during the installation so far as number and size of partitions to be created and how to do this.  I have the ubuntu install cd burned and ready to go (I have booted from the cd and the machine seems to like it fine)
Any thoughts/suggestions greatly appreciated.

Other responses have  not included the basic approach, which is very simple. If you are using the live CD and choosing install, that is  the GUI install, then one of the automatic  options will be to take over the whole drive and delete existing partitions I believe. This is simple, and may suit you for now. More elegant approaches can be used later, when you have gained more experience if you wish, either without a re install or with a reinstall.
hth

---

### Post by HenBar on 2007-07-13
Thanks for the replies and links, I think at this stage I will probably just install onto a single partition and then as I learn more, either create partitions or reinstall creating additional partitions.  I am sure I will be back with more questions.

Thanks again

---

