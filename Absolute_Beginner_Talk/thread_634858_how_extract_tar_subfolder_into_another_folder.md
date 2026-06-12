---
title: "how extract tar subfolder into another folder?"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by darck on 2007-12-08
I want to extract content of tar archive folder /media/disk into /media/disk path why it doesn't work?

sudo tar xvpfz backup.tgz media/disk -C /media/disk
- it seems ignoring -C/media/disk, because extracts all into /media/disk/media/disk instead into /media/disk (backup.tgz is located at /media/disk/backup.tgz )

---

### Post by adam.tropics on 2007-12-08
If you are already in /media/disk and you want it extracted right there, just do the 

sudo tar xvpfz backup.tgz

As it was, you told it to go to /media/disk, then change directory to /media/disk from there, hence /media/disk/media/disk.....I think!

---

### Post by darck on 2007-12-08
no,no,no
sudo tar xvpfz backup.tgz           extracts to  /media/disk/media/disk

If i can write tgz as directory:
i want extract:
/media/disk/backup.tgz/media/disk/        to          /media/disk/

---

