---
title: "Ubuntu 6.06 quick install made only 450 MB swap, how do i increase it"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by konungursvia on 2007-01-06
I have about 770 MB RAM, but the swap partition is not the recommended 2x that, I've tried increasing the size of the swap with GParted and actually from the windoze side using a popular partition manager but I am not allowed to increase its size in any of them. Do I need a larger swap? I have only noticed slight slowdown when running lots of apps, and one of them is usually Firefox, which is preset to hog rather a lot of RAM. Any suggestions?

---

### Post by jem7v on 2007-01-06
Well, between your RAM and your swap you Do have more than a gig of space to work with.  You actually have about the same amount (combined) as my computer does and I'm doing fine - so if you aren't dealing with Problems yet, it *might* be best to leave it alone. If you INSIST on changing the partition size, though, you might have luck using the GParted LiveCD instead of GParted from inside Gnome, but then again, it might run into the same issues.

But I'm not a recognized authority on these matters, so you might want to ignore me. Maybe.

---

### Post by housam on 2007-01-06
Normally swap partition is 2x RAM but not more than 1Gb. you can resize always using Gparted live CD. If you are not able to do it and don't have much data to care about , reinstall ubuntu after preparing your partitions manually.

---

### Post by konungursvia on 2007-01-06
Hmm. Okay, how do I download the image and burn it? for Gparted live cd I mean.

---

### Post by kill4killin on 2007-01-06
What are the disadvantages to having a swap of over 1GB? I have 2GB of RAM in my new system and so I made the swap the same size...is there a problem with it?

---

### Post by maniacmusician on 2007-01-06
this is a direct download link: [http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.3-0.iso?modtime=1165447791&big_mirror=0](http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.3-0.iso?modtime=1165447791&big_mirror=0)

their website is at [http://gparted.sourceforge.net](http://gparted.sourceforge.net)

To burn the image, just use Gnomebaker or K3b to burn an ISO. It's pretty straightforward, IIRC.

---

### Post by maniacmusician on 2007-01-06
> **kill4killin said:**
> What are the disadvantages to having a swap of over 1GB? I have 2GB of RAM in my new system and so I made the swap the same size...is there a problem with it?
If you have 2GB of RAM, swap is probably unnecessary and your system may even benefit by turning swap off. 

I don't know what exactly the disadvantage is; probably that with a space that big, it gets slow to load and write data to it, I'm not sure.

---

### Post by manutdfan2850 on 2007-01-06
seriously you wont need that much swap space anyway unless u have small ram to begin with.  u have 2gb of ram and unless u are doing heavy video editing or the like you wont need more than 512 mb and 1gb max of swap.

---

### Post by konungursvia on 2007-01-06
So if I use space from my linux partition, i don't need to defragment or anything like that?

---

### Post by konungursvia on 2007-01-06
So I only need to defragment ntfs and fat32 file systems?

---

### Post by maniacmusician on 2007-01-07
yeah, you don't need to defragment linux partitions. If you have to defrag your ntfs and fat32 systems, I'd recommend doing it while running windows so nobody blames a linux app for screwing up your windows partition.

---

### Post by macogw on 2007-01-07
> **kill4killin said:**
> What are the disadvantages to having a swap of over 1GB? I have 2GB of RAM in my new system and so I made the swap the same size...is there a problem with it?

I think I have 2GB swap and 1 GB RAM, though it seems my swap has been disabled :-/  When I type "free" it says I have no swap, but fstab says it's there *shrug* I think the 6.06 live cd called it an unknown file system instead of swap.

---

