---
title: "Listing partitions"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by phil66 on 2007-07-03
Ubuntu Dapper 

How do I call up hd's to get partitions and designated numbers for Ubuntu Dapper

In other words / or swap, etc

---

### Post by pbaumgar on 2007-07-03
On the command line, type:

df -h

---

### Post by phil66 on 2007-07-03
Is this saying everything on /dev/sdb1
Is there a way to expand to see the swap size ,etc

ray@ray-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              71G  2.5G   65G   4% /
varrun                505M   88K  505M   1% /var/run
varlock               505M  8.0K  505M   1% /var/lock
udev                  505M  124K  505M   1% /dev
devshm                505M     0  505M   0% /dev/shm
lrm                   505M   19M  487M   4% /lib/modules/2.6.15-28-386/volatile
ray@ray-desktop:~$

---

### Post by pbaumgar on 2007-07-03
try: fdisk -l

---

### Post by _alpine on 2007-07-03
I also have a little bit of a similar problem.  I have my partitions all set up and have a dual-boot with Feisty Fawn and Windows.  On my ubuntu desktop there are launchers for  NTFS and FAT32 shortcuts that I would like to delete but I can't.  Did I set up my partitions wrong or something?

Edit: Found my answer, haha.

---

### Post by phil66 on 2007-07-03
ray@ray-desktop:~$ fdisk -|
>

This what I get the greater sign

---

### Post by greg_g on 2007-07-03
Ignore this post, sorry, I thought I had an answer, but it didn't work for me.

---

### Post by phil66 on 2007-07-03
ray@ray-desktop:~$ fdisk -l
ray@ray-desktop:~$

This is results in lower case -l   Uppercase L lowercase l ????

---

### Post by pbaumgar on 2007-07-03
try it with sudo:  sudo fdisk -l (lower-case L)

---

### Post by niteshifter on 2007-07-03
Heres a few things that may help:

Try this with fdisk (that's a lower case L after the dash):
```
sudo fdisk -l /dev/sdb
```

To get a simple list of partitions:
```
cat /proc/partitions
```

With sfdisk you can get sizes in megabytes (also a lower case L):
```
sudo sfdisk -uM -l /dev/sdb
```

---

### Post by phil66 on 2007-07-03
Using sudo fdisk -l /dev/sdb gave me the info I was looking for 

Thanks to all

---

