---
title: "Access home folder in Windows and My Documents in Ubuntu"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by nirpius on 2007-10-08
I have added a separate partition for my home folder and formatted it as FAT 32 so that windows can read it but no matter what I have in my home folder, windows can only read the guest account and no matter what I put into it from Windows, I can never find it in Ubuntu.

---

### Post by hyper_ch on 2007-10-08
Do you have actually mounted that partition in Ubuntu?

---

### Post by nirpius on 2007-10-08
I don't know what you mean by mounted but if I log in as root and go to /home I can see my guest account, my own account etc. and I can access them but just not anything from Windows

---

### Post by hyper_ch on 2007-10-08
ok, from Linux with your normal user, can you read/write to that folder?

In Windows, as your normal user, can you read/write to that folder?

---

### Post by aquavitae on 2007-10-08
Just a suggestion, have a look at [http://www.fs-driver.org/]("http://www.fs-driver.org/").  You can use a linux partition (ext3) instead of fat32 and read it in windows, just install the windows driver.  Advantage is its a more stable file system, and fat32 often has permission issues because it doesn't really support permissions.

Aside from that, have a look for the following two files and post their contents: /etc/fstab and /etc/mtab.  The first lists the partitions that will be automatically mounted and the second lists the partitions that are currently mounted. "Mounted" just means that linux has read the partition nad has access to it.  Also, open a terminal and type ```
fdisk -l
```  This will list the all partitions you have on your computer and will probably be useful to post here so that anyone helping you can see how your system is set up.

---

### Post by macogw on 2007-10-08
> **aquavitae said:**
> Just a suggestion, have a look at [http://www.fs-driver.org/]("http://www.fs-driver.org/").  You can use a linux partition (ext3) instead of fat32 and read it in windows, just install the windows driver.  Advantage is its a more stable file system, and fat32 often has permission issues because it doesn't really support permissions.

Aside from that, have a look for the following two files and post their contents: /etc/fstab and /etc/mtab.  The first lists the partitions that will be automatically mounted and the second lists the partitions that are currently mounted. "Mounted" just means that linux has read the partition nad has access to it.  Also, open a terminal and type ```
fdisk -l
```  This will list the all partitions you have on your computer and will probably be useful to post here so that anyone helping you can see how your system is set up.

Why does "fdisk -l" get mentioned so much around here?  I see it asked for a *lot* but I get no output from that command.  To check that it's not just me I asked on IRC, and no output is a normal thing for that command.  df and mount show plenty of info, but fdisk -l doesn't do anything.

---

### Post by hyper_ch on 2007-10-08
actually it should be

```

sudo fdisk -l

```

or it must be run as root.

---

### Post by macogw on 2007-10-08
ahhh that does give output.  Thanks, guess that explains the mystery.

---

### Post by aquavitae on 2007-10-08
> **hyper_ch said:**
> actually it should be

```

sudo fdisk -l

```

or it must be run as root.

Yes, sorry.  I forget the sudo too often :)

---

