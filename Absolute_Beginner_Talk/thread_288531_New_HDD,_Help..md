---
title: "New HDD, Help."
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by thelocust on 2006-10-30
Ok so I started palying with linux on a 10 Gig HDD and now its filled up and Im ditching windows. I have a brand new 300 Gigger that I would like to eaither;

1: copy the image of my old HDD to the new one (partimage wont work because the old HDD is filled up so there's no room to write the image unless somebody knows how to tell it were to save the image.)

2: just make ubuntu think that the HDD got 300 Gigs bigger (some sort of raid thats not hardware supported, I dont have the gear for that)

Thanks to anyone who helps me out.](*,)

---

### Post by skydivingbiker on 2006-10-30
Are you using a dual boot system?

I already had ubuntu installed, but had a system problem.  I installed ubuntu from a CD and created new partitions.  When I logged in, I found hda1 and hda3 were still on the hard drive under the media folder.  So I didnt lose anything when I re-installed a 2nd time.

Took the computer an hour to re-partiton the 150gb seagate 7200rpm I've got.

There are prolly much better ways.. but that worked for me.

Now im gonna start backing up my system.

---

### Post by PWill on 2006-10-30
What you could do is put both HDDs in your computer, and then partition the new one as ext3 using a program like GParted: [http://gparted.sourceforge.net](http://gparted.sourceforge.net)

You could then boot back into Ubuntu, and mount the new HDD. Then you could just do something like
```
$ cp -R / /media/newhdd
``` (replace '/media/newhdd' with your new HDD'd mount point) :-D

---

