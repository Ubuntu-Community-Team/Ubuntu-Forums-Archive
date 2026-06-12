---
title: "can't partition vista any smaller"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Falc7 on 2007-12-11
I have made a partition to install ubuntu on in the vista disk management thing. But it won't let me make the ubuntu partition any bigger.
At the moment the two partitions are pretty much equal in size, but it won't let me shrink the vista partition any smaller, even though it has 50odd gb that aren't being used on it.
Vista also tells me that snapshots or pagefiles could limit how small i can make a partition, but gives me no clue as to what these are or how i get rid of them. 
please help

---

### Post by meborc on 2007-12-11
you can resize the partition inside ubuntu installer partitioning tool... as long as i know... but be sure the drive is defragmented many times and there is nothing at the end of it (that is where you resize it)

---

### Post by stchman on 2007-12-11
> **Falc7 said:**
> I have made a partition to install ubuntu on in the vista disk management thing. But it won't let me make the ubuntu partition any bigger.
At the moment the two partitions are pretty much equal in size, but it won't let me shrink the vista partition any smaller, even though it has 50odd gb that aren't being used on it.
Vista also tells me that snapshots or pagefiles could limit how small i can make a partition, but gives me no clue as to what these are or how i get rid of them. 
please help

You can only shrink the Vista partition so small.  What you can do is to uninstall any BS and defrag the drive.  Also turning off Vista's indexing can help.

---

### Post by Falc7 on 2007-12-12
Currently my vista partition is 71gb, with about 50odd gb free space, before i had it at 50gb in total.
I have refraged the drive, and turned off indexing, but it didn't help, how do i turn off

Vista tells me that snapshots or pagefiles could be the problem

---

### Post by meborc on 2007-12-12
> **Falc7 said:**
> Currently my vista partition is 71gb, with about 50odd gb free space, before i had it at 50gb in total.
I have refraged the drive, and turned off indexing, but it didn't help, how do i turn off

Vista tells me that snapshots or pagefiles could be the problemit was mentioned in another thread in cafe that vista has unmovable files in various places on the partition and that people have had problems resizing it smaller than 60gigs :( something with ghost unmovable files

---

### Post by CatKiller on 2007-12-12
> **meborc said:**
> something with ghost unmovable files

I'd imagine that if there's anything at all logical behind this, and it's not some stupid DRM nonsense, that it's just that these files can't be moved while the operating system that's using them is running. In which case, defragmenting as best you can and then using the Ubuntu installer to resize the partitions seems to be a sensible option.

---

### Post by meborc on 2007-12-12
you can always reformat the whole disk... create new partitions just the way YOU like them... then reinstall vista... and install linux

be sure to back up all your data beforehand :D

---

### Post by Falc7 on 2007-12-12
yep i think i will try that.
hm, hp didn't give me any installation disks for vista, they told me that if i needed to reinstall vista i could just get it back to factory settings with some kind of hp recovery tool or something. So it could be tricky.

As i have already installed ubuntu, is there a way to resize the partition with the ubuntu installer without taking ubuntu off, then putting it back on again?

---

### Post by Sef on 2007-12-12
> hm, hp didn't give me any installation disks for vista, they told me that if i needed to reinstall vista i could just get it back to factory settings with some kind of hp recovery tool or something. So it could be tricky.


Call them back and see if you can get the installations disks.  If you reformat the whole partition, it could wipe out the recovery partition.  Best to back up the whole disk, if you can.

---

### Post by CatKiller on 2007-12-13
> **Falc7 said:**
> As i have already installed ubuntu, is there a way to resize the partition with the ubuntu installer without taking ubuntu off, then putting it back on again?

Yes. Boot from the live disk and use GPartEd. They might have given it a friendlier name like "Partition Manager" or something. Make sure none of your partitions are mounted - there will be a lock next to any that are, meaning that you can't edit those ones. Resize to your heart's content.

---

### Post by stinger30au on 2007-12-13
> **Falc7 said:**
> yep i think i will try that.
hm, hp didn't give me any installation disks for vista, they told me that if i needed to reinstall vista i could just get it back to factory settings with some kind of hp recovery tool or something. So it could be tricky.

As i have already installed ubuntu, is there a way to resize the partition with the ubuntu installer without taking ubuntu off, then putting it back on again?

with hp machines there is a system restore creator icon on your desktop. run it and feed it some blank dvds and it will create recovery discs for you and will take you back to factory default if everything goes pear shaped

---

