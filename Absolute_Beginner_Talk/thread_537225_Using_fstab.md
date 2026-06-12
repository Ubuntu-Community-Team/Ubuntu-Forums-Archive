---
title: "Using fstab"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by shadowdance on 2007-08-28
I have these two lines in my fstab:

//molly/m /home/shadowdance/molly smbfs username=shadow,password=,gid=0 0 0
//molly/websites /home/shadowdance/websites smbfs username=shadow,password=,gid=0 0 0

The first line works perfectly - the network share is mounted... the second does not work - it says "only root can mount" when I try to open it...

Why?

---

### Post by lloyd_b on 2007-08-28
> **shadowdance said:**
> I have these two lines in my fstab:

//molly/m /home/shadowdance/molly smbfs username=shadow,password=,gid=0 0 0
//molly/websites /home/shadowdance/websites smbfs username=shadow,password=,gid=0 0 0

The first line works perfectly - the network share is mounted... the second does not work - it says "only root can mount" when I try to open it...

Why?

An experiment for you to try:  In a terminal window:
```
ls -ld /home/shadowdance/molly
ls -ld /home/shadowdance/websites
```

See if the two directories have the same owner and permissions.  I'm not an expert on Samba, but I *suspect* you have a permissions issue with the second directory.

Lloyd B.

---

