---
title: "advice needed for a laptop"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by housam on 2006-11-29
G'day every one,
I've bought a new laptop : HP Compaq nx7400 dual core T2500 (2.00GHz, 667MHZ FSB,2MB), 100G HDD,1GB RAM.
It comes with a win-xp pro as an original os copy on one partition 80G and another recovery image copy on a second partition 10G.
I want to ask if Dapper or Edgy is more suitable for my laptop and which of them is supporting dual core.(I've Dapper live CD)
For dual boot, I need to re partition the HDD, but do I've to format the win-xp partition first? or there is some way to do the task without deleting win-xp?

Thanks for the help

---

### Post by mcduck on 2006-11-29
No need for formatting. Just start the windows in safe mode and run defrag. After that Ubuntu's installer is able to shrink your windows partition and make some room for Ubuntu.

As for different versions, I suppose Dapper would be slightly more stable, but Edgy has a bit better support for different hardware (on my laptop, at least). The choice is pretty much yours. Both support multi core CPU's, Edgy out-of-the-box, and Dapper after you install package 'linux-686-smp'

---

### Post by housam on 2006-11-29
Thank you mcduck, 
Can I use the Geparted live CD for partitioning after defraging to shrink the win-xp partition?

---

### Post by 56phil on 2006-11-29
Housam, welcome to Ubuntu.:) 
> Can I use the Geparted live CD for partitioning after defraging to shrink the win-xp partition?

Yes you can. The install CD will take care of all your needs. Good luck.

---

### Post by zgornel on 2006-11-29
I don't think Gparted is a good solution for managing NTFS partitions (if you have such patition on your system). I'd go for a resize in windows using Norton Partition Magic. Never tested Gparted on a NTFS myself ;) ; if users are reporting no problem in resizing partitions with it, try it.

---

### Post by mcduck on 2006-11-29
Sure, you can use gparted cd to do it, but there really is no need as ubuntu installer can handle the job just as well, and gparted is also in the Ubuntu's desktop cd..

---

### Post by mblinux on 2006-11-29
A user had a succesfull install on your laptop with Dapper :
[http://www.ubuntuforums.org/showthread.php?t=287996&highlight=Compaq+nx7400](http://www.ubuntuforums.org/showthread.php?t=287996&highlight=Compaq+nx7400)

so I think that everything will be just fine. Dapper is great, but personally had no problems with Edgy too, on various machines. I'd like to suggest you Kubuntu, I'm a KDE supporter and I think that you could give it a try. 

Ubuntu + Gnome is really a top choice but I really like KDE.

---

### Post by housam on 2006-11-30
Thanks mblinux, it's a good link.
Thanks every body for the help. I'll notify after doing the installation.

---

### Post by radeon on 2006-11-30
get it back and buy somthing on core 2 duo not core duo unless you don't need 64bit.

---

### Post by mcduck on 2006-11-30
> **radeon said:**
> get it back and buy somthing on core 2 duo not core duo unless you don't need 64bit.

this far I haven't met a single person who would have any benefits from running on a 64 bit platform..

---

