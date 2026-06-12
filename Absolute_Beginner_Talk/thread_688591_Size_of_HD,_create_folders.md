---
title: "Size of HD, create folders"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by A dreamer on 2008-02-05
Hi,
I have installed Ubuntu 7.10 and have a HD with the size 164 Gbit (if I remember correct). I used the entire disk when installed Ubuntu and now I wonder how I can see how much space is used and not used? Also I would like to create a folder which could act as a "file server/backup" of files from my Windows PC and other Linux PC I have in my small local network. As it is now I can only create a folder inside my home folder.

BR,
Svein

---

### Post by wolfen69 on 2008-02-05
system>admin>system monitor>system

---

### Post by nick_h on 2008-02-05
To look at disk usage try:

Applications->Accessories->Disk Usage Analyser

At the command line you could use the *du* command.

To create a folder outside your home folder you will need root permissions.
```
sudo mkdir /mydir
```

---

### Post by A dreamer on 2008-02-05
Thanks a lot for the answer, it was very helpful.
Now I have created folders, but have no write permission to them. Do you know how to give users write access to the new folders outside the home directory?

BR,
Svein 

> **nick_h said:**
> To look at disk usage try:

Applications->Accessories->Disk Usage Analyser

At the command line you could use the *du* command.

To create a folder outside your home folder you will need root permissions.
```
sudo mkdir /mydir
```

---

### Post by nick_h on 2008-02-05
You will want to do two things:

1. Change the ownership and/or group of the directory.

First have a look at the curent permissions using:
```
ls -ld /mydir
```
It will be owned by root (listed first) and in the root group (listed second).

Change it with:
```
sudo chown myuser:mygroup /mydir
```

2. Change the permisions.

Permissions can be defined for the owner (u), group (g) and others (o).  The permissions can be read (r), write (w) and execute (x).

To begin with it will probably be:   drwxr-xr-x  meaning read/write/execute for the owner but only read and execute for the group and others.

Change it with:
```
chmod g+w /mydir
```

You can also use "a" to set "all".

For details type:
```
man chmod
```
and ```
man chown
```

---

