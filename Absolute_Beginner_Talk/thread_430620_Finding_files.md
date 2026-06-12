---
title: "Finding files"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by OscarL on 2007-05-02
Sorry about this really stupid question, but I just can't work it out (installed Ubuntu yesterday). How the heck do I find all my files? I want to reach my 2:nd hard drive. I'm in folder "/" but all I can see there is Ubuntu files (I think). What is the path to my other hard drive? Thanks!

---

### Post by bloodniece on 2007-05-02
I guess it depends on how it is mounted or if it is mounted at all.

Typically it may be in:

/media/hda2   perhaps?

---

### Post by bashologist on 2007-05-02
Open a terminal by going to -> Applications -> Accessories -> Terminal -> then paste the following text into the terminal window.
```
sudo fdisk -l
df -h
```Is this hdd internal or external? sata or pata?

---

