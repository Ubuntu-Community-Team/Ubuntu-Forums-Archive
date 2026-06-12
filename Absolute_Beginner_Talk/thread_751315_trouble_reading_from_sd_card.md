---
title: "trouble reading from sd card"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by slolerner on 2008-04-10
this past saturday i plugged in an sd card with recent holiday pictures and the os auto-magically recognized the card, mounted it as a new volume, and opened an "album" window. i copied off the fresh photos then unmounted and removed the sd card. the following evening i tried the same thing but got an error message.. could not mount the volume. the details said the os couldn't read a "superblock".

i made no changes inside the "album" window or to the camera and applied no system updates. the camera continued to write new photos to the card without issue.

i'm running gutsy gibbon 7.10 on a dell d420.. and the sd reader is built in.

any suggestions would be greatly appreciated. thanks in advance.

---

### Post by slolerner on 2008-04-10
good friend found a related thread from the forumns. i created a new directory and mounted the sd card volume:

sudo mkdir /media/sdcard
sudo mount /dev/sda1 /media/sdcard

and now i can find the sd card under places>computer>file system>media>sdcard.. but i don't see any of the photos. i can still view them through the camera.

is there a file format or file system disconnect?

again, any help would be appreciated.

---

### Post by El_Belgicano on 2008-04-13
I think it's because you didn't specify the filesystem type (-t vfat) in your mount command:
```
sudo mount -t vfat /dev/sda1 /media/sdcard
```

---

