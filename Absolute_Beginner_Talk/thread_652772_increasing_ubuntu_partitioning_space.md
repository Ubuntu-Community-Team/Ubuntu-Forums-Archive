---
title: "increasing ubuntu partitioning space"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by arvindenrique on 2007-12-29
[SIZE="3"]i installed ubuntu a week back and was sinply awestruck.

i installed it in 4gb space.

i also have windows installed in my system.

my questions are?

is there a way 2 increase hard disk space form taking some space from windows?

can free space can be merged from the ubuntu itself?

my windows partitioning is ntfs and ubuntu is on ext3

please do help me...[/SIZE]

---

### Post by eternicode on 2007-12-29
A Linux program like GParted can do this, but make sure you backup anything important first!  Also, you will want to boot into Windows and defragment your NTFS partition as thoroughly as possible.  [JkDefrag]("http://www.kessels.com/JkDefrag/") is a good tool for this.

Also, you can't re-partition the hard drive that Ubuntu is on *while* you're running that installation of Ubuntu, so you will need a Live CD that has the program on it (Ubuntu LiveCD should have it).

I'm going to assume that your drive partitioning looks something like this:
```

|                     |           |    |
|---------NTFS--------|---ext3----|swap|
|                     |           |    |

```

Once you have GParted open, and after it analyzes your disks, you will want to:

0) Make *absolutely positively sure* that you've backed everything up ;)
1) shrink your NTFS partition from the right; the measurements are in MiB (Mibibytes), which are basically the same as MB (Megabytes).
2) Move your ext3 partition to the left, snugly against the NTFS partition.  It's generally safer to add space to the end of a partition, rather than to the beginning of one.
3) Resize the ext3 partition to the right to take up the unallocated space.
4) click "Apply"

Let us know how it goes, and welcome to Ubuntu ;)

---

### Post by Sef on 2007-12-29
> i also have windows installed in my system.

Warning: If you have Vista, use the partitioner that came with it to shrink the partition.  If you have XP, use [GParted]("http://gparted-livecd.tuxfamily.org/") as mentioned above.

---

### Post by arvindenrique on 2007-12-29
this is how my partition looks like
file:///home/arvind/Desktop/Screenshot.png

---

### Post by arvindenrique on 2007-12-29
[IMG]file:///home/arvind/Desktop/Screenshot.png[/IMG]

---

### Post by zhouxing on 2007-12-29
sorry mate we couldn't see your screenshot. kindly make it as attachment (with clip button).

---

### Post by arvindenrique on 2007-12-29
[attach]54562[/attach]

---

### Post by zhouxing on 2007-12-29
> **arvindenrique said:**
> [SIZE="3"]i installed ubuntu a week back and was sinply awestruck.

i installed it in 4gb space.

i also have windows installed in my system.

my questions are?

is there a way 2 increase hard disk space form taking some space from windows?

can free space can be merged from the ubuntu itself?

my windows partitioning is ntfs and ubuntu is on ext3

please do help me...[/SIZE]

I just had a resize done to my ubuntu partition. Originally I gave 8GB and it soon runs to 7.5GB. So I enlarged it to 18GB. Now I have 10GB free space.

From your screen shot, I would suggest you to move all your data from /dev/sda8 to /dev/sda9 and use all spaces of /dev/sda8 to merge into your existing ext3 partition. By doing this, you won't lose the ubuntu you have already installed. But do backup your important datas before you go in case something wrong.

Simply delete /dev/sda8 and then resize /dev/sda7.

---

### Post by eternicode on 2007-12-29
> **zhouxing said:**
> From your screen shot, I would suggest you to move all your data from /dev/sda8 to /dev/sda9 and use all spaces of /dev/sda8 to merge into your existing ext3 partition. By doing this, you won't lose the ubuntu you have already installed. But do backup your important datas before you go in case something wrong.

Simply delete /dev/sda8 and then resize /dev/sda7.

This would be the easiest way to go, but, depending on what sda8 is used for, not necessarily the safest.

May I ask why you have five NTFS and two ext3 partitions?

Safer way to go would be to
0) backup, backup, backup :P
1) Shrink sda8 from the right by the amount you want to add to linux
2) Move sda8 to the right
3) Grow sda7 to the right to fill the gap
4) Hit "Apply"
This will keep the partition order and add space to linux.

But if you know that the data on sda8 can be moved without issues, by all means, transfer it to sda9, delete sda8, and grow sda7.

---

