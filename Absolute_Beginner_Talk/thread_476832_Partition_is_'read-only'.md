---
title: "Partition is 'read-only'?"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Alex Spencer on 2007-06-17
I'm a new user to Ubuntu, and I'm trying to delete files off another partition on my HDD which is not used for windows or linux, but it says the drive is 'read only'. What do I need to do? I've searched the forum but cannot find anything.

Thanks guys.
Alex

---

### Post by ugm6hr on 2007-06-17
> **Alex Spencer said:**
> I'm a new user to Ubuntu, and I'm trying to delete files off another partition on my HDD which is not used for windows or linux, but it says the drive is 'read only'. What do I need to do? I've searched the forum but cannot find anything.

What type of partition is it (NTFS / ext3 / ext2 / FAT)?

This will probably help:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

But if it doesn't just post the result of
```
sudo fdisk -l
```

---

### Post by Alex Spencer on 2007-06-17
Cheers, that tutorial looks good, I'll give it a go and post back if there are any problems.
Cheers for your help.
Alex

---

### Post by Alex Spencer on 2007-06-17
Thanks ugm, that tutorial worked a treat (it had a link to a program that sorted everything)
Alex

---

### Post by Citizin on 2007-06-17
Download a nice program called AutoMatix2, they have a tool that enables NTFS drives on linux for read/write.

---

### Post by Bluecircle on 2007-06-17
you probably need to install ntfs-config

```

sudo apt-get install ntfs-config

```

then run 

```

ntfs-config

```

Enable writing to internal/external drives.


EDIT: I lose.

---

### Post by Alex Spencer on 2007-06-17
Yeah ntfs-config is what I ended up using.
Cheers guys.

---

