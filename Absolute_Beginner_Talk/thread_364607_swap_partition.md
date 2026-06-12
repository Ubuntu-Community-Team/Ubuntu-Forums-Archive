---
title: "swap partition"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by saqib ku on 2007-02-18
I have made a new SWAP partition. Do i have to Mount it on Ubuntu manually or Ubuntu would mount it automatically. what is the procedure of manual Mounting.

---

### Post by taurus on 2007-02-18
You would add an entry in /etc/fstab to mount it each time you boot.  Assuming it's /dev/hda5, open a terminal and type

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hda5   none   swap   sw   0   0
```
Then, mount it with

```
sudo mount  -a
free
```

---

### Post by saqib ku on 2007-02-20
I opened the fstab but it already contains your code and Ubuntu System monitor shows 0 bytes of swap.

---

