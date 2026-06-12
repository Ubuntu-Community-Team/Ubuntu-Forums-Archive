---
title: "How do I make full backups?"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by henkk78 on 2006-06-09
Hi, 

I've now setup my Ubuntu system just like I like it. 

1. How can I make a full backup? 

2. Is there something similar to Norton Ghost for Linux? 

3. Also, can I make full backups without rebooting the system (as norton ghost does it)

Help will be greatly appreciated! 

Henk

---

### Post by hw-tph on 2006-06-09
1. Of the entire system? Either use dd or some more friendly tool such as [partimage](http://partimage.org/Main_Page).

2. See #1.

3. Use dd or tar.


Håkan

---

### Post by lkagan on 2006-06-09
I know of something that works exactly like Norton Ghost!  Uh, it's Norton Ghost!  :)  Ghost works on ext3 filesystems.  See more [here]("http://www.symantec.com/home_homeoffice/products/sysreq.jsp?pcid=br&pvid=ghost10").

Larry

---

### Post by steve.horsley on 2006-06-09
I always boot up a live CD, mount my Linux system partition and then make a tar file of the whole system (on a USB drive).

---

### Post by aysiu on 2006-06-09
[QUOTE=hw-tph]1. Of the entire system? Either use dd or some more friendly tool such as [partimage](http://partimage.org/Main_Page).[/QUOTE] There's a Ubuntu-specific tutorial for PartImage: [http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by mostwanted on 2006-06-09
Aysiu, how do you manage to make tutorials for everything under the sky? I want some of that magic pixie dust.

---

### Post by aysiu on 2006-06-09
As I said in another thread--I have Ubuntu elves... same way Santa Claus manages to deliver toys to children all around the world.

---

### Post by henkk78 on 2006-06-09
what about Keep? It came with Ubuntu...

However, I don't quite get the Linux filesystem. I plugged in the harddrive that I wanted to backup to. 

Then I started Keep and clicked "Add directory to backup". 

I typed in "/" as I want everything on the root partition to be backed up.

Then I realised, that my external harddrive will appear in the root partition (as /mnt/carrydrive/)

So therefore: a cyclical reference! 

I think the 'logical' linux way doesn't make as much sense as the 'physical' windows way of referencing harddrives and partitions... to me at least

---

### Post by aysiu on 2006-06-09
Well, there are pros and cons to each approach.

I like Linux's approach because it allows users to create a separate /home partition, which can appear to just be another folder within the / hierarchy but is really an entirely different, physically separate partition.

It may be possible to make C:\Documents and Settings an actual, physically different partition, but I've never heard of anyone doing that or explaining how to do that.

---

