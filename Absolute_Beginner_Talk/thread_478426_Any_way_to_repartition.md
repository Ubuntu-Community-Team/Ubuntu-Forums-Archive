---
title: "Any way to repartition?"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Wizdancer on 2007-06-19
So i downloaded and burned the ISO of Ubuntu (6.06) and i installed it all worked great, 
I didn't want dual boot so i partitioned it all to one big Ubuntu partition (or so i thought)
But after i start and i see... Oh the horror! I have 60 gigs + of space i cant use (Think its for windows since i can see it when i boot up)

So my question is: can i format the space to use with ubuntu?

Sorry if my english is bad. not my native tounge

PS. Ubuntu Rocks! ;)

---

### Post by dptxp on 2007-06-19
You can. Download Gparted, make Live CD and reformat.
You may have to remount the new one(s).

---

### Post by iceportal on 2007-06-19
Gparted is available in Synaptic (go to System->Administration->Synaptic Package Manager, type your password, search for 'gparted').

Also, the Gparted LiveCD is available at [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

Hope this helps!

---

### Post by LaRoza on 2007-06-19
I recommend the live cd, see my sig.

---

### Post by Wizdancer on 2007-06-19
If i do this, will i lose any data?

---

### Post by LaRoza on 2007-06-19
If you resize a partition, data should not be lost. There is a slight risk of data loss whenever you alter your partitions, so you should back up any essential data. I have never experienced data loss in this manner, and GParted is very stable and careful. I never heard anyone on this forum say they lost data during the resize, but it could happen.

When you resize a partition, make sure to either expand another parition to fill the space, or make a new partition, otherwise the space will be unused by your system. If you want to be able to share data between Linux and Windows, make a new partition and format it as FAT32.

---

### Post by dptxp on 2007-06-19
Why do you not post your details on partitions and make it more clear what you want ?

---

### Post by defrex on 2007-06-19
Also, any old Ubuntu live CD will come with Gparted, in case you don't feeling like burning another CD.

---

