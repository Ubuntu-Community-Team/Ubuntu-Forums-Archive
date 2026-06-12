---
title: "extra harddisk"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by EvilBro on 2007-11-23
I've recently added a harddisk to my ubuntu system. It was detected properly and can now be found in '/media' (or something like that) and I can access it. What I am however unable to do is create a folder on it by right clicking and selecting 'create folder' (the option isn't even there). I'm assuming this has something to do with permissions. Is this true? And if so, how would I make the harddisk available to all users?

---

### Post by TidusBlade on 2007-11-23
I always use root when I am there, try running "gksudo nautilus" in the terminal and it should launch nautilus as root, then try editing the HD. Furthermore, you can try right clicking the HD and changing it's permissions as root in nautilus. 
Hope it works ;)

---

### Post by Toet on 2007-11-23
Yep, changing the permissions is the way to go. I normally do this from the command line:

sudo chgrp -R <yourusername> /media/disk
(this changes the group to your user group)

sudo chown -R <yourusername> /media/disk
(this changes ownership to your user)

---

### Post by EvilBro on 2007-11-26
The permission thing has worked (but I guess you guys already expected that :) ). However, the disc isn't mounted automatically at startup (I mount it by using 'computer' as it is shown there). How do I tell ubuntu to mount the harddisk automatically?

---

### Post by Daveski on 2007-11-26
> **EvilBro said:**
> How do I tell ubuntu to mount the harddisk automatically?

You will need to add a line to your /etc/fstab file to tell Ubuntu to automatically mount this drive at startup. If you need help with this, please post your fstab and the results of

```
sudo fdisk -l
```

*NOTE: Sudo means this will run as root and therefore could be dangerous. Always be wary of people asking you to type commands such as the one above as if they are being malicious they could be asking you to destroy your data/installation. * fdisk -l (L is for List) asks the system to list disk partitions. If you are in any doubt as to the command you are running, try man <command> to find out what it does.

---

