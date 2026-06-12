---
title: "Partitioning using Xubuntu on Win98 PC?"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by mltom on 2008-02-23
I just purchased Xubuntu 7.10 to install onto my Dell Win98 PC.  

Question:  is it possible to create a partition using Xubuntu pgms onto my Win98 PC w/o losing my Win98 apps or re-formating the disk?

If its a problem, I'm ready to reformat the whold disk & just use Xubuntu.

this is my 1st post, thatnks in advance for your time.

tom

---

### Post by glennric on 2008-02-23
I am assuming that your windows partition is already using the whole disk.  In that case it is possible to do, but may not work.  You can use Partition Magic to resize the windows partition to a smaller size, if you are not using all of the existing partition.  Once that is done you can install Xubuntu in the rest of the disk.  However, sometimes partition magic messes up and then you can lose all of your windows partition.

---

### Post by bschleusner on 2008-02-23
You could also try gparted, I think that is on the xubuntu disk....

---

### Post by bobbybobington on 2008-02-23
I'm not 100% sure, but as long as Xubuntu uses the same partitioner as Ubuntu (gparted) you should be able to resize your win98 (fat32?) partition without destroying any of the data on it.

---

### Post by richaoj on 2008-02-23
during installation, you will be presented with many partitioning options -- there should be one that says "Guided - shrink partition and use free space"  you can go ahead and select this option and it SHOULD resize your current partition and then install ubuntu in whatever space it created.  HOWEVER, this very rarely messes up, so as with any new install, it is best to backup any vital data before you attempt it.  

But in your initial post, it seems as though you would not miss anything from the disk, so why not just try it.  It has a good chance of working, but if it doesn't, you can just wipe the disk and then re-install.  Good luck!

---

### Post by neurostu on 2008-02-23
A great third option is to download the GParted live cd (like partition magic just free). Use that to resize your partitions, then install xubuntu

---

### Post by mltom on 2008-02-24
Thanks to everyone.

I will be starting soon on this project & I'm sure you all will be hearing from me soon.     Remember all of this terminology is new to me ..

Thanks again

tom

---

