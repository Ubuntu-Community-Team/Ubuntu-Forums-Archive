---
title: "Dual Booting problems: partitioning"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by japtar10101 on 2007-07-08
Basically, I'm unable to Dual boot because the partition that Windows XP is using on our family computer (note: the rest of my family are near clueless about what an operating system is, let alone Linux) can't be resized for some reason.

At least, that's what I take is supposed to happen: I'm supposed to resize the main partition so I can fit a new partition to support Ubuntu.

Anyways, here's what the standard install window says about the partitions:

partition #1 (system recovery partition) |  FAT32 |  memory used: 1777MB
partition #2 (windows partition) | NTFS  |  memory used:  Unknown
free | memory left-over:  5MB

According to Windows Disk Defragmenter, I have 165GB of free space in my second partition.

When I try to edit partition #2, it doesn't even give me an option of resizing it.  It's almost as if the only options I have is to somehow fit Ubuntu in 5MB (yeah, right!), or to re-format partition #2!

What's up with that?  Is there a way around it?

---

### Post by zek725 on 2007-07-08
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by overdrank on 2007-07-08
HI just a thought can you unmount the drive and then resize it?

---

### Post by zek725 on 2007-07-08
> **overdrank said:**
> HI just a thought can you unmount the drive and then resize it?

yes. that's what should be done first.

---

### Post by japtar10101 on 2007-07-08
> **zek725 said:**
> [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

Wait a minute, the CD documentation didn't have that!  Was that from the Wiki?

Anyway, when I get to this window:
[http://img264.imageshack.us/my.php?image=feistydual12xc2.png](http://img264.imageshack.us/my.php?image=feistydual12xc2.png)

It doesn't give me an option to resize the biggest partition in the Hard drive.  What's up with that?

Also, how do you unmount and resize a harddrive?  I know programming, but I know near nothing about the technical parts of a computer.

---

### Post by overdrank on 2007-07-08
> **japtar10101 said:**
> Wait a minute, the CD documentation didn't have that!  Was that from the Wiki?

Anyway, when I get to this window:
[http://img264.imageshack.us/my.php?image=feistydual12xc2.png](http://img264.imageshack.us/my.php?image=feistydual12xc2.png)

It doesn't give me an option to resize the biggest partition in the Hard drive.  What's up with that?

Also, how do you unmount and resize a harddrive?  I know programming, but I know near nothing about the technical parts of a computer.

Ok I assume that you are installing Feisty 7.04. under system, admin , there should be gnome partition editor. Open gpart and try unmount  and resize the windows partition.

---

### Post by japtar10101 on 2007-07-08
> **overdrank said:**
> Ok I assume that you are installing Feisty 7.04. under system, admin , there should be gnome partition editor. Open gpart and try unmount  and resize the windows partition.

In liveCD???   Sorry, I forgot to mention that I still haven't installed Ubuntu yet (or once in my life, for that matter).

---

### Post by zek725 on 2007-07-08
> **japtar10101 said:**
> Wait a minute, the CD documentation didn't have that!  Was that from the Wiki? Nope. It's from a reliable source. I used that guide in my dual boot configuration. 

> Anyway, when I get to this window:
[http://img264.imageshack.us/my.php?image=feistydual12xc2.png](http://img264.imageshack.us/my.php?image=feistydual12xc2.png)

It doesn't give me an option to resize the biggest partition in the Hard drive.  What's up with that?

Maybe you should use [gparted]("http://gparted.sourceforge.net/"). Burn the ISO and boot from it. Unmount the partition. Assuming you have defragmented your partition before manipulating your partition, you can now resize your partition.

Here's a clearer procedure:
1. Defragment the partition you are about to resize.
2. Burn GParted into a disc.
3. Boot from GParted.
4. Select the desired partition to resize... (I guess you can work your way there).
Do not forget that the partition you are resizing should be the original filesystem (windows use NTFS as default).
5. After resizing the partition, you have a freespace. Then you can have Ubuntu automatically partition the freespace.

You can follow the guide i've posted before.

---

### Post by zek725 on 2007-07-08
> **japtar10101 said:**
> In liveCD???   Sorry, I forgot to mention that I still haven't installed Ubuntu yet (or once in my life, for that matter).

yes

---

### Post by japtar10101 on 2007-07-08
> **zek725 said:**
> Nope. It's from a reliable source. I used that guide in my dual boot configuration. 



Maybe you should use [gparted]("http://gparted.sourceforge.net/"). Burn the ISO and boot from it. Unmount the partition. Assuming you have defragmented your partition before manipulating your partition, you can now resize your partition.

Here's a clearer procedure:
1. Defragment the partition you are about to resize.
2. Burn GParted into a disc.
3. Boot from GParted.
4. Select the desired partition to resize... (I guess you can work your way there).
Do not forget that the partition you are resizing should be the original filesystem (windows use NTFS as default).
5. After resizing the partition, you have a freespace. Then you can have Ubuntu automatically partition the freespace.

You can follow the guide i've posted before.
50MB on dial-up....
*sigh*

But thanks, I found your sources very helpful!

---

### Post by overdrank on 2007-07-08
Hi I am at a lost here. Are you not trying to install ubuntu? DO you not have the live cd in place to install? If not then how do you know if you can not partition your drive?

---

