---
title: "Newbie attempting trying to partition"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by Acoustyk on 2007-10-04
Hey all, I'm completely new to linux and I'm trying to partition a 60 gig harddrive (Dell Inspiron 6000 laptop).  I've followed most of the guides around here but when I try to resize the sda2 partition it automatically aborts the resizing action and doesnt do anything.  I realized it wasn't mounted so I used "sudo mount /dev/sda2 /"  and after that it reported that the used amount on the partition was unknown so again I could not resize the partition.  

*This partition is an existing NTFS partition that my windows now operates on.  I do not want to lose this data but it is backed up.  I've made space on this drive and am prepared to allot 15 gigs for ubuntu"

Thanks for any help! :)

---

### Post by Acoustyk on 2007-10-04
btw if I ever get this working my planned partition is: swap: 2 gigs /: 2.5 gigs and /home: 10.5 gigs  

Does that sound good to everyone? (specs: 1.86 Ghz, 2 gigs RAM, 15 gigs from 60 gig HDD)

---

### Post by laidback on 2007-10-04
You cannot resize a partitiion that's mounted. Use the Live CD and System>Administration>Gnome Partition Editor (which is Gparted). It's a good idea to get hold of the Gparted Live CD which can be downloaded, ask Google to search for Gparted.

---

### Post by Siph0n on 2007-10-04
Whats the advantage of using the Gparted Live CD over the Ubuntu Live CD with Gparted? Thanks in advance! :)

---

