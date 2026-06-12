---
title: "resize ntfs partition"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by ronb94 on 2007-12-29
hello
i have 3 NTFS partitions i want resize 1 of them and ADD the free space to my linux partition.
how to do it?
Thanks

---

### Post by bindatype on 2007-12-29
One way to do this is to use gparted. If you don't have it installed then you can get it by
```

sudo apt-get install gparted

```
Run it and see if it recognizes the ntfs partitions. You ought to be able to shrink them and add the free space to your linux partition. 

Two things that have worked well for me are: 
1.) _Back_up_your_data_first!_ 
2.) I personally prefer to do this with the live boot CD. 

When windows comes back up (I assume you are running windows on your ntfs partitions) it will complain because its filesystem shrank unexpectedly. Just accept the defaults and allow windows to runs its diagnostics. You should be set.

---

### Post by ronb94 on 2007-12-29
i cant resize the partitions with the gparted:(:(
[IMG]http://img80.imageshack.us/img80/4646/screenshotdevsdagpartedlr1.png[/IMG]
what i am missing:confused::confused:

---

### Post by Moop on 2007-12-29
You need to unmount the partitions before you can resize them. If you right click on a partition there should be an option to unmount it. 

Also you should be working from the live cd to be able to unmount all your partitions.

---

### Post by ronb94 on 2007-12-29
i unmounted them but the only options i get after unmount are delete and format.

---

### Post by bindatype on 2007-12-29
This is why I said to use the live CD. You don't have to, depending upon the job at hand, but it does simplify things. To be clear, are you using the live CD or no?

---

### Post by ronb94 on 2007-12-29
ok i resized 1 of my ntfs partitions (on live cd) and now i have unallocated space what now how i add it to my et3 partition?
[IMG]http://img207.imageshack.us/img207/325/screenshotdevsdagpartedsn1.png[/IMG]

---

### Post by bindatype on 2007-12-29
Select the partition you want to grow and select resize--it is straightforward from there. If it asks you if you want to add the new space proceeding or following select following.

---

### Post by ronb94 on 2007-12-29
this is the window i got:
[IMG]http://img299.imageshack.us/img299/8707/screenshotresizemovedevsx5.png[/IMG]
none of the options(free space preceding and free space following)growing the partition i want.

---

### Post by ronb94 on 2007-12-29
someone:confused:

---

### Post by Moop on 2007-12-29
From the screen shot it looks like you didn't apply your changes yet. You might have to move the partitions around to get the free space next to the partition you want to add it to but I'm not real sure about that. 

Also you will need to unmount the partition you are adding the free space to. Make sure to click apply after making changes.

---

### Post by bindatype on 2007-12-29
Errm...did you mean to include a screenshot? Anyway, let's take it one step at a time and correct me if I am mistaken about my assumptions:

1.) You are trying to increase the space on /dev/sda3 with the space you just deallocated from some ntfs partition.

2.) You are actually running linux at the moment and I see that you only have one ext3 partition so this means that you must have _that_ partition mounted.

Please copy and paste this command in a terminal
```

mount

```

3.) I strongly suspect that you will find /dev/sda3 listed in the results. That means /dev/sda3 is mounted. However, you cannot change the size of /dev/sda3 when it is mounted--that's just the way it is. So you have to unmount /dev/sda3. The problem with that is that you are using it! Its a kind of catch-22. So to get around this problem you use the live CD. 

The live CD will run ubuntu and gparted in particular _without_ mounting /dev/sda3. This allows you to resize it with no problems. 

Gparted is part of the live CD so it will be very simple once you boot into it. And Moop is absolutely correct about applying the changes. In principle, you can spread out a partition over a physical volume but it isn't recommended.

---

### Post by ronb94 on 2007-12-29
1. yes
2. No, i am using livecd now.
I applied changes after I took some GB from ntfs partition.but still i cant add the unallocated space to my ubuntu partition, with resize/move i can just take space from the partition i cant add.
[IMG]http://img180.imageshack.us/img180/2663/screenshotresizemovedevhx7.png[/IMG]

---

### Post by bindatype on 2007-12-29
This is a pain but try shuffling your partitions so that the unallocated space is adjacent to your ext3 partition. Gparted is trying to prevent spreading the ext3 partition over physically distinct sectors on your disk,

---

### Post by bindatype on 2007-12-29
This link ought to help explain the usage [http://www.howtoforge.com/partitioning_with_gparted_p2]("http://www.howtoforge.com/partitioning_with_gparted_p2")

---

### Post by ronb94 on 2007-12-29
i didnt undertood how to move the partition. and if i understood right i have to place the unallocated place near the /dev/sda3.Am i right?

---

### Post by ronb94 on 2007-12-29
bumb

---

### Post by bindatype on 2007-12-29
Yes, you want the unallocated space to be adjacent to sda3. DId you find the link I posted helpful?

---

### Post by ronb94 on 2007-12-29
Thank you very much its worked:)

---

### Post by bindatype on 2007-12-30
I'm very happy to hear that.

---

