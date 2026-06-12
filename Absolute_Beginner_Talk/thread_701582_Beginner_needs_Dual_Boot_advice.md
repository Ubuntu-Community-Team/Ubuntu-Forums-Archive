---
title: "Beginner needs Dual Boot advice"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Neil_The_Newbie on 2008-02-19
Beginner needs help with Dual Boot Setup

I have been using Ubuntu for about a year and have just purchased a new laptop (FUJITSU SIEMENS AMILO PI-2515) that has Windows Vista pre-installed on it. I have NO installation disks only a recovery disk that I made. The laptop has a 160GB hard drive and it appears to be partitioned as follows: System C: 91.4GB and Data D: 45.7GB. I have installed Autocad 2007 on the laptop also. My questions are:

1)I want to create it as a dual boot system (as I will be using Ubuntu the most) so I need to know how do I go about installing Ubuntu on it (I have a CD from a magazine with the latest version of ubuntu on it). 
2)I will only be using the windows partition for CAD and occasional web browsing what should the partition sizes be and how do I change them? 
The laptop spec can be found here: [http://www.comet.co.uk/cometbrowse/product.do?sku=435848&tab=specification#spec](http://www.comet.co.uk/cometbrowse/product.do?sku=435848&tab=specification#spec)

I'm still a newbie with the technical side of things but i love the ubuntu and opensource ethos.

---

### Post by Paqman on 2008-02-19
First of all, thoroughly defrag your existing partitons, and back everything up.

You'll need to shrink one of those partitions down and create some space for Ubuntu. It's probably best to use Vista's own partition manager for that, since Gparted hasn't been tested extensively with Vista.

You only need 10GB for Ubuntu, max. Keep your data on the 45GB NTFS data partition and it'll be available in both OSes.

If you're just doing a basic install you can pop the Ubuntu disk in and tell it to use the unformatted space you created. It'll create a root and swap partition automatically in that space. Job done.

---

### Post by myddewji13 on 2008-02-19
watever u do ...do not use gparted to format/shrink a vista partition if u wanna dual boot....cuz vista hates it when u do...trust me i tried and had to reinstall from my recovery disk + start all over.... 5 hrs later

---

### Post by Neil_The_Newbie on 2008-02-19
thanks for that. how much space do you recommend for the windows partition?

---

### Post by Paqman on 2008-02-21
Take a look at how much space is already used on the Windows partition, and give it at least 20% extra above that. You need to have free space on there to avoid massive file fragmentation from degrading performance.

---

