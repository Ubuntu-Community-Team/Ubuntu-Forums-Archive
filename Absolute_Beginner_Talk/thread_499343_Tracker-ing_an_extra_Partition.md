---
title: "Tracker-ing an extra Partition"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by Matuku on 2007-07-12
I recently installed Tracker (and Affinity but its tracker thats causing issues) but can't work out how to get it to index my NTFS partition where all my files are stored for easy access for both windows and ubuntu work. Is this supported or am I simply going about it incorrectly? The partition is mounted at /media/sdb1 but I entered this in the watched location list with no luck.

---

### Post by Matuku on 2007-07-13
Bump

---

### Post by annda on 2007-07-13
i don't know if tracker supports ntfs, but you can check it at least intends to index the drive

```
grep sdb1 /home/yourusername/.Tracker/tracker.log
```

i added tracker to my startup sessions with the following options and it seems to work (but they are not ntfs):

```
trackerd -i /usr -i /media/sda6 -i /media/sda8 -i /media/ARCHIWUM
```

---

### Post by Matuku on 2007-07-16
Seems to have sorted itself out now; maybe it was just taking a while to index the files/

---

### Post by kbchoi on 2008-03-17
I have the same issue with Gutsy Gibborn. Most of my data files are stored in NTFS partition, so I can share with my WinXP. But tracker does not work for them. Would this be the permission issue? (My NTFS partition is owned by root.) Please help.

---

### Post by bruce89 on 2008-03-17
Surely adding /media/whatever to the "additional paths" list would work. System>Preferences>Search and Indexing>Files. I suppose it could be a permission thing, I don't know what user *trackerd* runs as.

---

### Post by forrestcupp on 2008-03-17
> **bruce89 said:**
> Surely adding /media/whatever to the "additional paths" list would work. System>Preferences>Search and Indexing>Files. I suppose it could be a permission thing, I don't know what user *trackerd* runs as.

That works for me.  I've been indexing my Vista Users folder for quite some time now without trouble.

---

