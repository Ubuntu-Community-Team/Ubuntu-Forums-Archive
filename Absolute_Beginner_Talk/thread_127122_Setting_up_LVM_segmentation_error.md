---
title: "Setting up LVM: segmentation error"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by Bubba Ho-Tep on 2006-02-08
I've a couple of questions on this - first off I'll explain what I'm trying to do 

I've 3 IDE drives (x2 80Gbs and x1 160Gb) and I want to mirror around 100Gb of data (my system drive isn't one of these)

I was thinking of making an LVM volume out of the 2 80s and then RAID1 that with the 160Gb

Should I do this or (if it's possible) should I RAID1 the drives and then make an LVM volume out of them? LVM on RAID as opposed to RAID on LVM I suppose.

Next question -
I followed [this](http://www.gentoo.org/doc/en/lvm2.xml) tutorial - the most up to date and understandable one I could find (the [TDLP](http://www.tldp.org/HOWTO/LVM-HOWTO/index.html) one I didn't understand much of) and after a lot of mucking about managed to create 
a physical vol
a volume group
a logical vol
stick a filesystem on it
but then when it came to mounting the logical vol I got a "segmentation error" from mount.

The 2nd and subsequent mount attempts saw the terminal hang on the mount command.

Google didn't turn up anything, so does anyone here have any ideas?

I can't seem to find any easy way of undoing all the creating of vol groups etc I did so I can start from scratch, so I am tempted to wipe my system drive and install Ubuntu again (its a relatively new install) as i saw some stuff on LVM in the partitioning bit of the install. Would this be worth it or should I persevere?


BHT

---

### Post by Bubba Ho-Tep on 2006-02-12
No-one? Should I repost this in another forum here?

---

