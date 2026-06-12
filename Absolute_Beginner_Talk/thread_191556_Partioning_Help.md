---
title: "Partioning Help"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by chrism66 on 2006-06-07
I have a 120GB hard drive with 1 GB Ram. What would be the best partioning scheme for this hard drive (Ubuntu only system)

Thanks,
Chris

---

### Post by johnc4510 on 2006-06-07
I use three partitions:
/   which is the system root       10GB
/swap   which is a swap file         1024mb
/home   where all your home(personal)files are located   The rest of my drive

---

### Post by Blondie on 2006-06-07
This is merely my opinion,

10 GB /
2 GB swap
The rest /home

10 GB for / is plenty, and you've got the space. If you're going to install lots of programs, even games, it will still probably be enough.

There isn't really such a thing as too much swap but it should generally be twice your RAM memory. More than that may increase performance in theory, but only infinitesimally.

/home is for your personal files, videos, pics etc. so give it everything that you don't need for other purposes.

---

### Post by chrism66 on 2006-06-08
Ok thanks for the help. 

Now I have a question. I have a /home/chris directory on both the / and /home partion. If I want o save to the /home partion how do I go about doing that?

---

### Post by carlosqueso on 2006-06-08
Are you sure that you have the directory on both partitions?  Linux file systems retain their structure regardless of what drive or partition (or even machine if you use NFS), they are on.  Thus, even though /home/chris is under /  it is on the /home partition.  I hope that makes sense.

---

### Post by aysiu on 2006-06-08
You may want to look at this:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by wpshooter on 2006-06-08
[QUOTE=Blondie]This is merely my opinion,

10 GB /
2 GB swap
The rest /home

10 GB for / is plenty, and you've got the space. If you're going to install lots of programs, even games, it will still probably be enough.

There isn't really such a thing as too much swap but it should generally be twice your RAM memory. More than that may increase performance in theory, but only infinitesimally.

/home is for your personal files, videos, pics etc. so give it everything that you don't need for other purposes.[/QUOTE]

I believe I would dedicate a bit more to the root / directory, just in case Ubuntu came up with some innovation that might require a good bit more space.  Better to have a bit to much than to come up short.  Of course, this would subtract from what you had to store other stuff but you would still have in the 100gb range.

---

### Post by az on 2006-06-08
I'm a fan of the default - all on / plus a swap.

---

### Post by hajk on 2006-06-08
...and I like to mount /boot on a small (64MB) ext2 partition by itself, possibly not even mounted automatically....:)

---

### Post by az on 2006-06-08
[QUOTE=hajk]...and I like to mount /boot on a small (64MB) ext2 partition by itself, possibly not even mounted automatically....:)[/QUOTE]
... at the beginning of the drive if you are running very old hardware who's bios cannot see any more than the first few gigs of your disk and would leave your system unbootable if you installed another kernel image that was put farther up on the disk....

---

