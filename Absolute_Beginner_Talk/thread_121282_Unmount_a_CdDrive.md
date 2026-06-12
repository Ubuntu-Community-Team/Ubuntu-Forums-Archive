---
title: "Unmount a CdDrive"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by Kevbb on 2006-01-24
Hi,
I loaded up the kubuntu desktop following instructions below:
```

sudo apt-get cdrom add
sudo apt-get install kubuntu-desktop

```
all went fine, but now I go to do an update using "sudo apt-get update"
it appears to be trying to load info from a CD, rather than the repositories list.
e.g. code starts off as below
```

sudo apt-get update
Ign cdrom://ubuntu 5.10 breezy Badger_ release i.386 (20051012) Breezy release.gpg
...etc
And errors =
failed to fetch cdrom...etc

```
Any help would be greatly appreciated, as then I can tell if my previous problem is fixed.

Many thanks / Kevbb.

---

### Post by Sutekh on 2006-01-24
All you need to do is comment (or remove) the line in your repository list that looks for the CD-ROM.
```
sudo gedit /etc/apt/sources.list
```
(Assuming you still have gedit, if not use kate instead)
And comment (#) the line that contains the CD-ROM repository.  It will be the line that starts with 'deb cdrom'.

Save and retry
```
sudo apt-get update
```

---

### Post by Kevbb on 2006-01-24
Cool that worked a treat....thanks.

---

