---
title: "[SOLVED] ext3 partition on external hard drive"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by guitarj1d on 2008-03-31
After creating a 138 gb ext3 partition on the end of my 500gb ntfs external hard drive, it says 7gb are being used.  I don't see any files on the partition.  The only folder is lost and found with nothing in it.  Where did these 7gb's go?

---

### Post by scragar on 2008-03-31
mount the partition, then check everything on it, see what you've got:
```
ls -AhlRS **MountPoint** | less
```

---

### Post by guitarj1d on 2008-03-31
This is what it gives me:

/media/disk:
total 16K
drwx------ 2 root root 16K 2008-03-30 19:56 lost+found
(END) 


however, when I right click on the drive, and click properties it says 138.6 gb total, 7.2 gb used.  In gparted it says 140.81 gb total 2.39 used.  Why does each method give me a different number?  Which is correct?

---

### Post by Inxsible on 2008-03-31
I think that the 7 GB is used up to store the filesystem. Ext3 is a journaling filesystem and it does take up some space on the drive. 7GB out of 138 seems about right.

I formatted a 500GB to EXT3 and I got 485GB available. So 15 Gigs was used up.

---

### Post by mrsudo on 2008-03-31
I agree with Inxsible.
if you really want to find out though just reformat it.  
since you have nothing on there, you dont really have much to lose.

---

### Post by guitarj1d on 2008-03-31
All right, thanks guys.  One more quick question.  My other partition is ntfs, and since you don't use a windows machine anymore I want to put all of my data on ext3.  Can I move directly from the ntfs partition to the ext3 partition or do I have to copy to my computers hard drive first, and then copy it over to the other partition?

---

### Post by Inxsible on 2008-03-31
> **guitarj1d said:**
> All right, thanks guys.  One more quick question.  My other partition is ntfs, and since you don't use a windows machine anymore I want to put all of my data on ext3.  Can I move directly from the ntfs partition to the ext3 partition or do I have to copy to my computers hard drive first, and then copy it over to the other partition?

It would be the same still right, since your computer's partitions will also be EXT3(assuming your computer has Ubuntu on it).

In short, you can copy over directly

---

### Post by guitarj1d on 2008-03-31
Thanks for your help.

---

### Post by stchman on 2008-03-31
> **guitarj1d said:**
> After creating a 138 gb ext3 partition on the end of my 500gb ntfs external hard drive, it says 7gb are being used.  I don't see any files on the partition.  The only folder is lost and found with nothing in it.  Where did these 7gb's go?

The EXT3 filesystem does have some overhead around 5% I believe.

---

