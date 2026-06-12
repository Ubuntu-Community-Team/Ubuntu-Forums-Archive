---
title: "partition problems"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by rbhigday on 2007-01-15
I desire to add to partitions to my current hard drive but gparted will not let me do it live nor will it let me do it with the disk. I tried using the live disk and it did not find my monitor.

Any suggestions or am I stuck.

Also would I be able to do this via usb port on my laptop if I take the hd out of my desktop?

---

### Post by Sef on 2007-01-15
> I tried using the live disk 

Do you mean you used Ubuntu's Live CD or the GParted Live CD?

---

### Post by bodhi.zazen on 2007-01-15
> **rbhigday said:**
> I desire to add to partitions to my current hard drive but gparted will not let me do it live nor will it let me do it with the disk. I tried using the live disk and it did not find my monitor.

Any suggestions or am I stuck.

Also would I be able to do this via usb port on my laptop if I take the hd out of my desktop?

Can you give more details?

I would assume either you have no free space or you are at the limit of 4 primary partitions.

If you want more then 4 partitions, one must be extended (that is 3 primary and one extended).

The extended partition may then contain additional logical partitions.

See here:

[http://www.ubuntuforums.org/showthread.php?&t=282018](http://www.ubuntuforums.org/showthread.php?&t=282018)

---

### Post by rbhigday on 2007-01-15
> **Sef said:**
> Do you mean you used Ubuntu's Live CD or the GParted Live CD?

at that time the gparted live since then both :)

---

### Post by rbhigday on 2007-01-15
> **bodhi.zazen said:**
> Can you give more details?

I would assume either you have no free space or you are at the limit of 4 primary partitions.

If you want more then 4 partitions, one must be extended (that is 3 primary and one extended).

The extended partition may then contain additional logical partitions.

See here:

[http://www.ubuntuforums.org/showthread.php?&t=282018](http://www.ubuntuforums.org/showthread.php?&t=282018)

Hard drive sda I have

```
1 ntfs partions 127.99
unallocated 25.39 (i wonder about this because this does not show on the windows side)
```

hard drive sdb i have
```
ext3 143.26
extended 5.79
linus-swap 5.79
```

hard drive sdc i have

```
fat16 1.91

```
all sizes are gigs


I am trying to reduce the ext3 partions on sdb to create a storage and transfer partition.

btw attaching to the laptop was also a no go ](*,)

---

### Post by bodhi.zazen on 2007-01-15
Well, how goes it ?

As long as you are house-cleaning ....

Your Swap partition could likely be reduced, I usually advise 1 Gb max :p

Make sure sdb is **not mounted**, then resize ....

Once the ext3 partition is smaller you should have some free space. You can move the swap to consolidate the free space ....

The you should be able to create your partitions.

HTH 8)

---

### Post by rbhigday on 2007-01-16
> **bodhi.zazen said:**
> Well, how goes it ?

As long as you are house-cleaning ....

Your Swap partition could likely be reduced, I usually advise 1 Gb max :p

Make sure sdb is **not mounted**, then resize ....

Once the ext3 partition is smaller you should have some free space. You can move the swap to consolidate the free space ....

The you should be able to create your partitions.

HTH 8)

err dumb question, if I unmount it while using it wont ubuntu crash?

I thought swap parts was suppose to be 2 times ram, which for me would be 4gb swap since i have 2 gb ram?

---

### Post by bodhi.zazen on 2007-01-16
> **rbhigday said:**
> err dumb question, if I unmount it while using it wont ubuntu crash?

I thought swap parts was suppose to be 2 times ram, which for me would be 4gb swap since i have 2 gb ram?

1. You should partition/resize from a live CD, either the Ubuntu desktop CD or the Gparted live CD. 

You will not be able to re-size a partition if it is mounted ...

2. Ram X2 is "old school" and from the days when RAM was much smaller. Depending on what applications you run  you are likely never to use swap with 4 Gb RAM. You would need to sue some heavy duty video applications ....

Type ```
free
``` in a terminal to see how much RAM you are actually using ....

---

### Post by rbhigday on 2007-01-16
> **bodhi.zazen said:**
> 1. You should partition/resize from a live CD, either the Ubuntu desktop CD or the Gparted live CD. 

You will not be able to re-size a partition if it is mounted ...

2. Ram X2 is "old school" and from the days when RAM was much smaller. Depending on what applications you run  you are likely never to use swap with 4 Gb RAM. You would need to sue some heavy duty video applications ....

Type ```
free
``` in a terminal to see how much RAM you are actually using ....

Thanks for the info I will chop the swap and repartion tonight when I get home.
Will have to use the laptop since the live cd do not work fine on my pc. glad the laptop is "stable" for once, never was with windows

---

### Post by mikewhatever on 2007-01-16
Pardon me if this is partly of topic. Having 1GB of RAM I made 920MB swap partition, and was much surprised to discover that it is never used. I suppose the only time it's put to action is when suspend or hibernation modes are entered.

---

### Post by bodhi.zazen on 2007-01-16
> **mikewhatever said:**
> Pardon me if this is partly of topic. Having 1GB of RAM I made 920MB swap partition, and was much surprised to discover that it is never used. I suppose the only time it's put to action is when suspend or hibernation modes are entered.

LOL that is not off topic, that is my point.

If you would like to do some reading look here:

[http://www.linux.com/guides/sag/swap-allocation.shtml](http://www.linux.com/guides/sag/swap-allocation.shtml)

[http://www-128.ibm.com/developerworks/aix/library/au-satswapspace.html](http://www-128.ibm.com/developerworks/aix/library/au-satswapspace.html)

Enjoy 8)

---

### Post by rbhigday on 2007-01-16
anyone know how long it take to repartition a drive?

I went from a 142g to a 100 gig and it going on 2 hours to do that. I got a bad feeling about this!!!!

---

### Post by rbhigday on 2007-01-17
well It finished sometime thru the night and booted with no problem. gave up waiting after 3 hours and went to bed :)

---

### Post by bodhi.zazen on 2007-01-17
LOL, thanks for the follow up.

Glad it turned out OK :)

---

