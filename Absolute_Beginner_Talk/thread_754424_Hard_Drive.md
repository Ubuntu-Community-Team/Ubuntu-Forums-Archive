---
title: "Hard Drive"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by DaMann on 2008-04-13
I have been dual booting Ubuntu with Windows XP for a while now. I have a 230GB hard drive. I partitioned the whole thing for Windows originally. Then when I got Ubuntu I partitioned 50GB for that. I just realized that there is almost no space left on the partition for Windows. I don't have much stuff on here either. I have 36.4GB used on Windows and not many at all on Ubuntu. It tells me I have 16.7GB left on Windows. I am now getting started in electronic music and those programs can take up a few gigs so I would like to get this figured out soon.

Thanks
-DaMann

---

### Post by oilchangeguy on 2008-04-13
> **DaMann said:**
> I have been dual booting Ubuntu with Windows XP for a while now. I have a 230GB hard drive. I partitioned the whole thing for Windows originally. Then when I got Ubuntu I partitioned 50GB for that. I just realized that there is almost no space left on the partition for Windows. I don't have much stuff on here either. I have 36.4GB used on Windows and not many at all on Ubuntu. It tells me I have 16.7GB left on Windows. I am now getting started in electronic music and those programs can take up a few gigs so I would like to get this figured out soon.

Thanks
-DaMann

you've not asked a question. just made a statement. according to your statement you've used less than 100gb on a 230gb hard drive. so where's the other 130 gb's?

---

### Post by DaMann on 2008-04-13
> **oilchangeguy said:**
> you've not asked a question. just made a statement. according to your statement you've used less than 100gb on a 230gb hard drive. so where's the other 130 gb's?

Oh my bad. Yes pretty much...I am missing 130GB and I don't know why. Does anyone know why this could be so or how to fix it?

Thank you
-DaMann

---

### Post by DaMann on 2008-04-14
Daily bump ^.^

---

### Post by oddin85 on 2008-04-14
how did you partition your hard drive? you can check to see if there's any unallocated space.
if you have gparted installed run:
```
sudo gparted
```

if you don't have gparted installed, then run this first:
```
sudo apt-get install gparted
```

this will give you a window that looks like the screen shot i've attached. you can see where i have some unallocated space, but it's only a little bit, so i'm ignoring it untill 8.10 comes out

in order to change the partition table i think you need to be running gparted off the live cd because the hard drive would be in use otherwise

****don't forget to backup any data that's in the hard drive you're going to be partitioning****
(i learned the hard way :-()

---

### Post by Inxsible on 2008-04-14
Put in the Live CD. Open up GParted and see what drives you have and what partitions you have.

Sometimes there can be dual drives, so they need to be selected from the top right corner of the GParted window.

Post a screenshot here...if you have any more questions.

---

### Post by DaMann on 2008-04-14
> **Inxsible said:**
> Put in the Live CD. Open up GParted and see what drives you have and what partitions you have.

Sometimes there can be dual drives, so they need to be selected from the top right corner of the GParted window.

Post a screenshot here...if you have any more questions.

Ok I'll do that in a bit, I'm having fun with Madtracker right now =D!

---

