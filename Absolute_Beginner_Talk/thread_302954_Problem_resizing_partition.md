---
title: "Problem resizing partition"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by muleaga on 2006-11-19
Hallo all,

I'm trying to enlarge my second partition (/dev/sda3) but Resize option in Gparted does not work.
I attached Gparted screenshot.

Thank You.

---

### Post by muleaga on 2006-11-19
Sorry. I forgot to attach screenshot in first post. ](*,)

---

### Post by ajgreeny on 2006-11-19
This is because you can't move the start of a partition backwards on the disk.  You will need to copy/backup the whole partition, remake a new larger one with the unallocated space included, and then paste the copy back to the new bigger partition.  I'm not sure if gparted will do that, but you can use partimage for the backup part and then go from there.  Good luck.

---

### Post by cotcot on 2006-11-19
Another possibility might be reducing the sda3 by storing data elsewhere untill its size is less that the free (unallocated space). Than you can move sda3 with the "move" command of parted, resize it with (g)parted and restore data you might have stored elsewhere.

---

### Post by CatKiller on 2006-11-19
> **muleaga said:**
> I'm trying to enlarge my second partition (/dev/sda3) but Resize option in Gparted does not work.

The version of GParted in the repositories is quite old, and doesn't have full move support. In particular, it doesn't allow you to move the start of an ext3 partition.

The latest version of GParted, available on the [GParted live cd]("http://gparted.sourceforge.net/livecd.php"), **does** have full move support. Try that instead.

---

### Post by cotcot on 2006-11-20
You will not be able to move your sda3 with (g)parted because of the overlap between the new location and the old location of sda3. That is why I recommended to reduce it to less than the unallocated space before moving. Here is the relevant section of the parted manual : [http://www.gnu.org/software/parted/manual/html_node/move.html]("http://www.gnu.org/software/parted/manual/html_node/move.html")

---

### Post by CatKiller on 2006-11-20
It doesn't matter if the free space is smaller than the existing partition if you are **resizing** the partition by moving the start point of the partition. Here is the relevant section of the GParted documentation : [http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

And from the [GParted news page]("http://gparted.sourceforge.net/news.php"): > 04 September 2006 : GParted 0.3

It took a bit longer than expected, but finally we decided to release GParted-0.3.
This release includes one of the most exiting features since the first release;
We finally have full move support!! ...

---

### Post by muleaga on 2006-11-20
Thanks all for helping. 
Cotcot is correct. Moving sda3 partition before resizing is not possible (I tried it :-k  and overlapping error occurred).
It looks like I will have to backup my data and create new partition or resize it to available Unallocated Space and than move it.

---

### Post by muleaga on 2006-11-20
> **CatKiller said:**
> It doesn't matter if the free space is smaller than the existing partition if you are **resizing** the partition by moving the start point of the partition. Here is the relevant section of the GParted documentation : [http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

And from the [GParted news page]("http://gparted.sourceforge.net/news.php"):

Sorry. I didn't see this post. It looks like you are correct. My gparted was older version (0.2.5). I downloaded and compiled 0.3.1 and it looks like I can resize partition to left unallocated space. I will try it later and report my progress.

Thanks all.

---

### Post by housam on 2006-11-20
> Sorry. I didn't see this post. It looks like you are correct. My gparted was older version (0.2.5). I downloaded and compiled 0.3.1 and it looks like I can resize partition to left unallocated space. I will try it later and report my progress.


Hi, try to take a screen shot of your partitions before resizing by :
# sudo fdisk -l
you will need it in case something goes wrong.
take care while resizing because I've lost some data while doing this with Gparted.
Good luck

---

### Post by muleaga on 2006-11-20
Me again... ;) 
Resizing with Gparted 0.3.1 worked perfectly. I successfully added unallocated space to my sda3 partition.

Thanks...

---

