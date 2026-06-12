---
title: "No Disk Space Left - Merge Partitions?"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by Franks&amp;Beans on 2006-07-10
I have no disk space left on my root partition (thanks to Ubuntu's auto partition installer:( ) so it won't let me log on to the gnome desktop. Can only get to failsafe terminal. Anyone know of a way I can merge my root partition with another free partition without losing evrything?

Thanks.

---

### Post by aysiu on 2006-07-10
If both partitions have data on them, then, no.

In failsafe terminal, try this ```
sudo apt-get clean
```

---

### Post by Franks&amp;Beans on 2006-07-10
Thanks - sudo apt-get clean didn't seem to do anything. I want to merge the root partition with a completely free partition (ie. no data on it)Merge or resize that is - only problem is the partitions are on the same disk but not following each other.

I know partition Magic for Windows can do this - is there a Linux equivalent?

Thanks.

---

### Post by aysiu on 2006-07-10
That command I gave you was supposed to free up considerable space by cleaning out the /var/apt/cache/archives folder of all the installer .deb files from Synaptic/apt-get/aptitude.

Still not enough disk space?

---

### Post by user1397 on 2006-07-10
> **aysiu said:**
> If both partitions have data on them, then, no.

In failsafe terminal, try this ```
sudo apt-get clean
```where was that folder that that command you provided cleans up?  (sorry for the mal-constructed sentence)

EDIT: never mind, I reloaded firefox too late :(

---

### Post by Franks&amp;Beans on 2006-07-10
Thanks - the "clean" did free up enough space for me to get the gnome desktop working again.

Problem still exists though - I need my root partition to be bigger (is only 2GB) The auto partitionor of Ubuntu created a 2GB / drive and a 7GB /home drive.

Anyway, I think I still need a program that can merge linux partitions. Is this right? or is it going to be a reinstall?:(

---

### Post by aysiu on 2006-07-10
You could *move* a folder to its own separate partition.

These instructions are specifically for moving /home to its own partition, but I'd imagine the instructions would be the same for /usr, too:
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

