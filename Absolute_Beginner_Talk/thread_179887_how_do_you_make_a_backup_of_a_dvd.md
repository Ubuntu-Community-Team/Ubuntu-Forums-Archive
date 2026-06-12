---
title: "how do you make a backup of a dvd?"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by shutupimpoor on 2006-05-20
I need to make a backup of my windows recovery disk. I have been looking all over for dvd copying software, can anybody help me?](*,)



Edit:

[QUOTE=manicka]the easiest way is to right click on the disc when it mounts on the desktop and choose 'copy disc', then select 'copy disc to' file image.

When the iso file image is made you can right click on it and choose 'write to disc'[/QUOTE]

easiest route. Thanks!

---

### Post by aysiu on 2006-05-21
Have you tried K3B, Gnomebaker, or Graveman?

---

### Post by jazzmuzik on 2006-05-21
This might be worth a try (on the command line):

Insert recovery disk and go to a directory with at least 4.5 gig of free space:
```
dd if=/dev/dvd of=dvd.iso
```
insert blank dvd and:
```
growisofs -Z /dev/dvd=dvd.iso
```

---

### Post by shutupimpoor on 2006-05-21
i am very new to this, terminal freezes when i try the commands. do i have to do like cd somedirectory? then what?

---

### Post by jazzmuzik on 2006-05-21
You have to cd to a directory (partition actually) that has at least 4.5 gig of free space. Use 'df -h' to see where your free space is.

The first command copies the entire dvd to disk. Did it really freeze or was is working? It takes some time to get it done. Was the hard drive light on indicating it was receiving the data from the dvd?

---

### Post by manicka on 2006-05-21
the easiest way is to right click on the disc when it mounts on the desktop and choose 'copy disc', then select 'copy disc to' file image.

When the iso file image is made you can right click on it and choose 'write to disc'

---

### Post by shutupimpoor on 2006-05-21
[QUOTE=manicka]the easiest way is to right click on the disc when it mounts on the desktop and choose 'copy disc', then select 'copy disc to' file image.

When the iso file image is made you can right click on it and choose 'write to disc'[/QUOTE]

easiest route. Thanks!

---

