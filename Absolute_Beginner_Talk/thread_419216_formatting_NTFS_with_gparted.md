---
title: "formatting NTFS with gparted"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by t00th on 2007-04-22
I have a USB external hard drive which is currently unformatted, and have been trying to use gparted to format it to NTFS.  The option is greyed out, and I have no idea why.

---

### Post by taurus on 2007-04-22
Is your external harddrive mounted right now?  You cannot format a drive when it's mounted so you need to unmount it first before you can format it.

```
df -h
```

---

### Post by t00th on 2007-04-22
It isn't mounted.  I have the option to format it in a bunch of other filesystems, but NTFS is greyed out.

---

### Post by click4851 on 2007-04-22
I believe there is additional packages in Synaptic that add NTFS support to gparted, I had to add that to copy and resize my WinXP partition.

---

### Post by az on 2007-04-22
I think you need this.  

[http://packages.ubuntu.com/feisty/otherosfs/ntfsprogs](http://packages.ubuntu.com/feisty/otherosfs/ntfsprogs)

---

### Post by click4851 on 2007-04-24
thanks az, I think that is the package....or he could download the gparted live cd. That should have ntfs support.

---

### Post by marx2k on 2007-11-01
> **az said:**
> I think you need this.  

[http://packages.ubuntu.com/feisty/otherosfs/ntfsprogs](http://packages.ubuntu.com/feisty/otherosfs/ntfsprogs)

Awesome. That's exactly what I needed to format to NTFS in gparted. Thank you!

---

