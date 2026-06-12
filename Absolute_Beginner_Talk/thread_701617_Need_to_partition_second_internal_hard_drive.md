---
title: "Need to partition second internal hard drive"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by McFugger on 2008-02-19
I am a total n00b to Ubuntu, i have two 160GB internal hard drives and after installation of gutsy 7.10 i only have access to one since i think only one was partitioned because did not do in manually. How to i change it so i can access my second hard drive?

---

### Post by Het Irv on 2008-02-19
You can try using the Partition Manager on the Live-Cd. First, I would go to Places->Computer and check the properties on File system to see how much space it is taking up.  It may already be using the full 320GB, or close to it since you need room from / and swap.

---

### Post by jken146 on 2008-02-19
I doubt it will be using both drives.  Anyway, you can use the live CD, but it's probably quicker to install the same partition editor in your installed Ubuntu.
```
sudo aptitude install gparted
```
Then run it: ```
gksu gparted
```
Then you can look at both your drives, and partition the second one as necessary.

The next step is to mount each new partition somewhere permanently.  You'll need to edit /etc/fstab as descibed [here]("http://www.psychocats.net/ubuntu/mountlinux").

---

### Post by housam on 2008-02-19
type in a terminal ```
sudo fdisk -l 
``` 
and post the result please where -l is a small L

---

### Post by Fred_E _krugar on 2008-02-19
The best way to do this is download this ISO and burn it cd [http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads)
and boot from that , and do whatever you need to do.

---

### Post by McFugger on 2008-02-20
Thank you. got it going using partition editor.

---

