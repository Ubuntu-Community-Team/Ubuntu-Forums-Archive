---
title: "Mirror IDE drives: Poor man's NAS"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by abasel on 2007-08-29
I'm wanting to build a poor man's NAS and have two questions:
1) Can Ubuntu be configured to Mirror IDE disks and if so how?
2) Can I use the desktop version or should I use Server?

:popcorn:

---

### Post by asmoore82 on 2007-08-29
If you want to mirror with the hard drives connected to the same computer,
Use the Ubuntu LiveCD or something lighter like Gentoo Minimal if you want and do some form of a dd command like ...
```
~ $ dd if=/dev/hda of=/dev/hdb
```

If you want to keep the drives in seperate machines and use the network download
some form of UDPCast ... [http://udpcast.linux.lu/bootmedia.html](http://udpcast.linux.lu/bootmedia.html)

---

### Post by expatCM on 2007-08-29
A very interesting topic .....  nice to see the question.

I wonder why mirroring drives is considered to be a poor man's NAS.  If you have say four 500GB drives for storage then the real cost is in the drives and not the board and chip which are effectively the only missing components.

I have been carefully thinking about this (talk and thinking cost nothing) and really think it is best to bite the bullet and build a NAS.  There is free software to run a NAS  [http://www.freenas.org/](http://www.freenas.org/) and from the total hardware perspective there is not really much to it (depending on how you configure everything).

The beauty is that you have a stand alone (and potentially portable) device.

The headache which I have not really faced yet is what exactly to do about proper data backup.  Yes, if you set up a RAID 5 then individual hardware failure can be managed but what about loss of the box as a whole.

If you are resolute in looking at backing up individual drives directly then perhaps this link may interest you
[http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

---

### Post by abasel on 2007-08-30
Thanks for that, your feedback is great and I will look at those links later.

Just to answer why I call it a poor man's NAS. I  saw a product sold here in NZ which was very neat with a whole lot of bells and whistles but it cost $900 for  2x 250gb Drives... that makes it cheaper to by a computer and use it instead. Now I have some old PCs lying around and harddrives are cheap. Therefore when compared to the above product, his works out much cheaper (although not as portable).

Backups are a problem. With the advent of digital photos and video, protecting family memories is a really  problem. This end fire is a threat while in SA theaft would be. These threats could be reduced for the NAS by hiding it in a secure place removed from water and fire threat.

---

