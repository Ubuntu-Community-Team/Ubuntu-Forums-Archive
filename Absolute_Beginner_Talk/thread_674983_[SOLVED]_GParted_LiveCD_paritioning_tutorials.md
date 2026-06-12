---
title: "[SOLVED] GParted LiveCD paritioning tutorials?"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2008-01-22
Can any one point me to a simple tutorial or guide or how to use the GParted LiveCD to partition an Ubuntu disk?
Thanks.

---

### Post by kellemes on 2008-01-22
You can use the Ubuntu livecd also.. As far as I know there is a partition-editor (GParted) installed.
By the way, I see no problem with the mirror.. it works for me but you can also use the torrent they provide.

---

### Post by Bartender on 2008-01-22
If I had broadband I would post some guides on YouTube or whatever.  
If you have broadband I'd suggest downloading/burning the GPartedLiveCD.  I think it works better than an Ubuntu LiveCD.
[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

Some pointers -
Right-click on the partition you want to modify.  If that doesn't work, try right-clicking on the text description below the map.

Apply one task at a time.  Don't stack up several tasks and ask GPLCD to do them all at once.

What is it you're trying to do?

---

### Post by kleo skywalker on 2008-01-22
I downloaded the GParted iso, going to burn it now.
I want to pull out some space from my /home partition.

---

### Post by p_quarles on 2008-01-22
Good, easy to follow tutorial here:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

That uses the Ubuntu live CD, but the procedure is the same for the Gparted live disk.

---

### Post by Desperate on 2008-01-22
Hi Just discovered that there are updates already for G parted so install those too, before you start editing, might prevent a less nice experience :)

---

### Post by kleo skywalker on 2008-01-22
> **p_quarles said:**
> Good, easy to follow tutorial here:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

That uses the Ubuntu live CD, but the procedure is the same for the Gparted live disk.

Thanks.
I'm not trying to create a separate /home though - I already have a separate /home. I just want to free some space from it. The instructions will probably work, so I'll try it and post back.

---

### Post by oldos2er on 2008-01-22
> **kleo skywalker said:**
> Can any one point me to a simple tutorial or guide or how to use the GParted LiveCD to partition an Ubuntu disk?
Thanks.

 [http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by rosegarden78 on 2008-01-22
I don't know about *tutorial* per se but to launch program in any Ubuntu flavor even Blackbox use a terminal or konsole or press Alt-F2.  Then simply type **gparted**, g-parted or any executable file such as shell script.  You should see the GUI pop up shortly.  As far as what to do from there:

A disk drive is like a pizza.  You slice it into partitions.  From the beginning you have the choice to make an initial slice or leave it alone.  This called Primary and Extended partition.  I do not suggest making an Extended partition.  This will make moving and resizing partition impossible.

**Make all partitions primary.**

So when you want to install Ubuntu make sure it doesn't say Use All Disk Space.  You need to manually split your Primary (WIndows?) partition into the size you see fit.  Generally a 50/50 split will work.  I used an 80/20 split with Windows only having 7GB!  Make sure both partitions are primary.

Now the Ubuntu Installation should automatically handle it from there.

---

### Post by kleo skywalker on 2008-01-24
It was easy. Had to choose the "force VESA" option for the LiveCD to boot though.
I wanted to shrink a partition; it took a long time but worked alright.
Thanks.

---

