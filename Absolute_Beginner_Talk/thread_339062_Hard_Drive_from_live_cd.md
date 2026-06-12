---
title: "Hard Drive from live cd"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by gloscherrybomb on 2007-01-15
Hi,

I was using photorec to try and desperately recover some lost photos and it wrote 60gb of date to my harddrive. Now it wont let me log in because it says I'm out of space.

Using the live cd, how can I access my home folder and remove some of the files to make space? I cant seem to find it, only the ubuntu folder in place of my username.

---

### Post by Iarwain ben-adar on 2007-01-15
Hiya,
try this
```
 sudo fdisk -l
mkdir ~/recovery
sudo mount /dev/hdX,Y ~/recovery

```

Where X,Y is the hard drive and partition: e.g. /dev/hda2

Then you can remove some files from your hard disk :wink:


Iarwain

---

### Post by gloscherrybomb on 2007-01-15
Works a treat thanks!

---

### Post by DigitalDingo on 2007-01-22
I'm trying to do the same, however it needs a filesystem type:

$ sudo mount /dev/hda2 ~/recovery
mount: you must specify the filesystem type

What shall I do?

---

### Post by Iarwain ben-adar on 2007-01-22
Are you sure it is the correct name?
If you are, try this:
```
sudo mount -t ext3 /dev/hda2 ~/recovery
```


Iarwain

---

