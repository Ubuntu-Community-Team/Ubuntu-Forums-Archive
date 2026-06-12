---
title: "Disk partitions"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by ayazrkhan on 2007-05-28
I want to resize the partition on my HDD.  I have three partitions: ext3, Fat32 and NTFS.  What is the best way of doing this.  Thanks in advance for any help.:confused::confused::confused:

---

### Post by oilchangeguy on 2007-05-28
> **ayazrkhan said:**
> I want to resize the partition on my HDD.  I have three partitions: ext3, Fat32 and NTFS.  What is the best way of doing this.  Thanks in advance for any help.:confused::confused::confused:

you can run from the live cd, and use gparted.

---

### Post by ayazrkhan on 2007-05-28
I want to resize my HDD partitions.  I have 3 existing partitions: ext3, FAT32 & NTFS.  What is the best way of doing this?  Would prefer a GUI based solution.

Thanks in advance.

Ayaz

---

### Post by ayazrkhan on 2007-05-28
Thanks.  I can do this even though I have Feisty installed?

---

### Post by merlinus on 2007-05-28
Gparted live cd from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

If you are wanting to install Ubuntu, there is a disk partitioning screen during that process.

Good luck!

-merlin

---

### Post by ayazrkhan on 2007-05-28
Merlin,
Thanks.  I have Feisty running, just want to resize.  Would the gpartition live CD still work?

---

### Post by Hobo Joe on 2007-05-28
You could also install Gparted with:
```

sudo aptitude install gparted

```

---

### Post by taurus on 2007-05-28
> **Hobo Joe said:**
> You could also install Gparted with:
```

sudo aptitude install gparted

```

You cannot resize partition (Feisty) while you are using it.  Has to be done from the LiveCD.

---

### Post by Hobo Joe on 2007-05-28
> **taurus said:**
> You cannot resize partition (Feisty) while you are using it.  Has to be done from the LiveCD.

d'oh! *smacks forehead*

---

### Post by ayazrkhan on 2007-05-28
Thank you everyone for all your help.

will revert with results.. 

AK

---

