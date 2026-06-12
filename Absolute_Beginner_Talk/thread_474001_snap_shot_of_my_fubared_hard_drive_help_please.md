---
title: "snap shot of my fubared hard drive help please"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-06-14
Pretty messed up huh? can you help me fix it please?

---

### Post by swoll1980 on 2007-06-14
back too the top i go

---

### Post by drs305 on 2007-06-14
Glad to see you found out how to post the image.  I'm back and can help some. Any experts feel free to jump in here.

Is there anything on /dev/sda2 that you might want to save?

If not, then we can unmount /dev/sda2, run gparted and then expand /dev/sda3 to incorporate the extra space freed from sda2. 
Will you have access to the forum while you are running gparted. Eventually to increase and move the root directory you will have to unmount it (exiting ubuntu). You'll have to run gparted from a gparted CD or the ubuntu live CD.  If you just want to create another partition and leave root alone, it will be easier and you can stay on ubuntu.

---

### Post by swoll1980 on 2007-06-14
dont want to save anything just want clean install/ fresh hard drive. Thanks for advice earlier by the way

---

### Post by swoll1980 on 2007-06-14
i will have access to forum

---

### Post by drs305 on 2007-06-14
If you want to start over completely, I'd recommend you take a look at the following link:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

There is a good discussion of how to set up your hard drive. I'd recommend a root partition of about 10-15GB, a swap partition of 1-2GB (depending on your memory) and the rest as /home. Lots of opinions around about the sizes. You'll have to run the installation from the beginning and set it up when you get to the partitioning section.

If you just want to get a new partition with 17GB, this will be very easy and we can get it done online.

If you have data on this computer please back it up onto some other drive or media if possible and let us know where it is located on your current hard drive.

---

### Post by swoll1980 on 2007-06-14
that would be fine as long as i can save file on it

---

### Post by drs305 on 2007-06-14
> **swoll1980 said:**
> that would be fine as long as i can save file on it

I think what you said is that it would be okay just to make a new partition. To do this:

Unmount /dev/sda2 and then start gparted
```

sudo umount /dev/sda2 &
sudo gparted

```

When gparted starts, click on the black /dev/sda2 box.
Select Partition, Format to, and the format you want (probably ext3)
You may be warned that any data on this partition will be lost.
Let gparted format the partition. When it's done, close gparted.

You will now have a new partition (dev/sda2) that is formatted to ext3. Once you have done that, we will edit your fstab to allow you, the user, to read and write to it.

If you understand, go ahead and do the above and when you are done formatting the new partition,
let us see your fstab:

Back it up first:  (edited to include sudo)
```

sudo cp /etc/fstab /etc/fstab.bak

```


Then we will edit it.
```

gksudo gedit /etc/fstab

```

Copy the results here so we can take a look at it. 

If I don't answer right away, it's because a thunderstorm is bearing down on our city and I may have to shut my computer down!

---

### Post by swoll1980 on 2007-06-14
doing it now

---

### Post by Hobo Joe on 2007-06-14
> **swoll1980 said:**
> dont want to save anything just want clean install/ fresh hard drive. Thanks for advice earlier by the way

If you just want a clean install you could just run the install disk and click the option that says 'use entire disk'.

That SHOULD format the whole thing and partition it properly.(correct me if I'm wrong anyone)

---

### Post by swoll1980 on 2007-06-14
cp /etc/fstab /etc/fstab.bak      (permision denied)

---

### Post by drs305 on 2007-06-14
> **swoll1980 said:**
> cp /etc/fstab /etc/fstab.bak      (permision denied)

My bad, it should be:

```
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab
```

---

### Post by swoll1980 on 2007-06-14
i got it, had to delete all partitions restart.Then run cd guided use entire disk

---

### Post by drs305 on 2007-06-14
That will make the best use of your entire drive. Happy ubuntu-ing!

---

