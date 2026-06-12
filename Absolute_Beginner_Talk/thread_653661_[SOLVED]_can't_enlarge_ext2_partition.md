---
title: "[SOLVED] can't enlarge ext2 partition"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2007-12-30
Hi,
I know there are plenty of threads regarding this topic but nowhere i found something that matches what i want to do unfortunately :(.

I have attached a screenshot of gparted.

I'm running Gparted from Gutsy LiveCD and what i've done by now was to shrink /dev/sda8 and thus resulted the unallocated 3.62GB space. What i want to do now is to enlarge the ext2 partition but i can only shrink it! It just doesn't "see" the unallocated space when trying to use "Resize/Move" on ext2 partition. I found [this]("http://ubuntuforums.org/showthread.php?t=618785") thread but i don't wanna mess up with fstab and stuff in order to manually repair GRUB ... isn't there an easier way to do this?

What i've noticed so far is that the ext2 partition doesn't see the unallocated space. The only partition that sees the unallocated space is the one i've shrinked in order to make available this space (that is /dev/sda8 ).

Best regards and any attempting to help is appreciated!

---

### Post by Liolikas on 2007-12-30
Delete that swap partition.
When job done leave some space for new swap.
And you can make 2-4 times smaller swap.

---

### Post by arvindenrique on 2007-12-30
u cant enlarge the partition size in the ubuntu itself.u go to windows and format both linux swap and ext2 partition.u have to note only successive partitions can be merged.so delete and format the partiton /dev/sda8 and also backup ur data before doing it.
    Now all the 3 partitions will be merged.from this create new partitons of new size and install ubuntu and enjoy

---

### Post by Liolikas on 2007-12-30
The is no need to stick on whindos you can use:
[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by the_nomad on 2007-12-30
> u cant enlarge the partition size in the ubuntu itself

neither if i'm using the LiveCD? everywhere says that should work by using Gutsy LiveCD or gparted LiveCD...

> The is no need to stick on whindos you can use:
[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

so you're saying that gparted LiveCD would allow me to do more things that i can do with Gusty LiveCD?



LE: i swapped off the swap partition ... or at least this was i meant to do until gparted crashed. I guess now i have to reinstall ubuntu and be more careful when partitioning :) Thats something i'll really enjoy this time rather than be freaked off i may lose data ... of course i will backup first! BACKUP BACKUP BACKUP !!!

---

### Post by Liolikas on 2007-12-30
No there is no difference.

Just remove swap at first as I said in my first post.

---

### Post by the_nomad on 2007-12-30
Dude thanx alot!!!
Ok so i've swapped off, deleted the swap partition in order to bring the unallocated space besides ext2 partition, and now it worked to resize it! So i used the "Resize/Move" from the menu of ext2 and simply enlarged it, and also moving it to the left in order to make the swap partition the last in the list. Right now the gparted looks like in the screenshot i've attached.

thanx again!


LE: as a conclusion to all those searching threads that might show them how to resize i think the following sentence will clear some things up: "you can't **enlarge** a partition unless the **unallocated space** is right next to it! you can however shrink a partition, resulting new unallocated space next to it!"

---

### Post by insane_alien on 2007-12-30
the ext2 can't be resized because the free space is before it. if you move the partition to the free space first you should be able to do something from there.

you might want to look at lvm2 as that makes moving partitions about really easy.  also makes things really easy if you add a drive or two.

---

