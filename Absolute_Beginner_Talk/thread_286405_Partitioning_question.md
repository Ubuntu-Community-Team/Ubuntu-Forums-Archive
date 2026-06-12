---
title: "Partitioning question"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by chimerical_brio on 2006-10-27
Alright, hypothetical situation. Let's say I wanted to try out one of the BSD operating systems, just for kicks, but didn't want to completely wipe my computer. Obviously, I would make a partition. Now, let's say I absolutely HATE BSD and realize that Ubuntu is the best thing for me (which would probably be the case; I don't have a lot of patience). Would it be possible (using Gparted or whatever) to then wipe that partition that I created for BSD and bring it back from the dark side to Linux again? Thanks a lot.

---

### Post by bulldog on 2006-10-27
Yes you could using the live cd,cause you can't repartition with mounted hdd's.

---

### Post by po0f on 2006-10-27
chimerical_brio,

You could do it from the commandline, just:
```
# mke2fs -j /dev/XdYZ
```
where X designates either an IDE (h) or SATA/SCSI (s) drive, and Y designates the drive (a for first, b for second, and so on), and Z designates the partition (1, 2, etc).

The above command just formats the partition as an ext3 filesystem, clean as a whistle.  Make sure you get it right though.  ;)

---

### Post by bodhi.zazen on 2006-10-27
> **po0f said:**
> chimerical_brio,

You could do it from the commandline, just:
```
# mke2fs -j /dev/XdYZ
```
where X designates either an IDE (h) or SATA/SCSI (s) drive, and Y designates the drive (a for first, b for second, and so on), and Z designates the partition (1, 2, etc).

The above command just formats the partition as an ext3 filesystem, clean as a whistle.  Make sure you get it right though.  ;)

Err...

I think the CLI would be:
```
sudo fdisk hda
```

And the CLI will not resize or move partitions.

Gparted, as suggested by Bulldog, from the live CD, is best.

---

### Post by po0f on 2006-10-27
bodhi.zazen,

I would hope the partition is already created if BSD used to be installed on it.  In that case, you would just format it, ie run mke2fs on it.

---

### Post by bodhi.zazen on 2006-10-27
> **po0f said:**
> bodhi.zazen,

I would hope the partition is already created if BSD used to be installed on it.  In that case, you would just format it, ie run mke2fs on it.

LOL: :lol: po0f, your answer is a fine one indeed. Very knowledgeable and I am not trying to criticize you (in fact I am impressed you have knowledge of the CLI).


However, the question, to my eye anyway, was how to partition. First create one for BSD, then if BSD is deleted resize back to Ubuntu.

Also BSD uses UFS so mke2fs will not help much.

Peace be with you,

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by chimerical_brio on 2006-10-27
Indeed, I was looking to figure out the best way to partition (considering I know just about nothing about all of this). Thanks so much, I really feel like I know how to go about this now (I'm going to try it with the LiveCD). Thanks again!

---

### Post by JayTee on 2006-10-27
If you want to do it fairly easy just download the Gparted LiveCD from 
[http://gparted.sourceforge.net](http://gparted.sourceforge.net). It's an ISO file (it's about 28.5 MB) you just burn the image to disk and it's bootable. Boot from it and that will allow you to run the partition editor to delete the BSD partition(s) and resize the Ubuntu partion to reclaim the space for Ubuntu.

---

