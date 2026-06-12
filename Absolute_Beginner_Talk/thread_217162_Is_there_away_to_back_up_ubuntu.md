---
title: "Is there away to back up ubuntu?"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by kris2pe on 2006-07-16
I find that installing xgl is hard.
It actually ruined my setup twice.
So is there procedure do it?

---

### Post by reacocard on 2006-07-16
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by orb9220 on 2006-07-16
What if I want to backup my /home or root the tut says the partition to be backed up should be unmounted and the backup to drive should be mounted.

Won't unmounting my root or /home have ill effects or keep me from doing commands. such as sudo partimage ?

Thanks yer help is appreciated.

---

### Post by reacocard on 2006-07-16
the tutorial also suggests doing it from the **_LiveCD_** for that reason. your root and home are unmounted already, so they can be safely backed up.

---

### Post by nofreerides on 2006-07-16
> **kris2pe said:**
> I find that installing xgl is hard.
It actually ruined my setup twice.
So is there procedure do it?

I just did installed XGL / Compiz successfully and here's how I did it [http://nofreerides.blogspot.com/2006/07/setup-xglcompiz-on-ubuntu-and-have.html](http://nofreerides.blogspot.com/2006/07/setup-xglcompiz-on-ubuntu-and-have.html)

When you get it to work and if you decide to remove it then simply go to /etc/gdm/gdm.conf-custom , open the file, delete ALL of the text in the file, save it. And restart your computer.  If you setup "thefuture" to start automatically, as shown in the Ubuntu forum for setting up XGL/Compiz, then you'll want to not have it start automatically.

For the cube snapshot I used ksnapshot set with a 10 second timer which gave me enough time to get the cube in the position I wanted it for the snapshot.

---

### Post by nofreerides on 2006-07-16
> **kris2pe said:**
> I find that installing xgl is hard.
It actually ruined my setup twice.
So is there procedure do it?

I did some searching and this link looks the most promising and the easiest [http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

I haven't tried it yet but it's basically a snapshot of Ubuntu file system starting with / and excludes some folders you don't want suchc as /media.

---

