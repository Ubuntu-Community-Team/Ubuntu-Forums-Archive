---
title: "finding my a: drive"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by rickycodie on 2007-05-10
well i have a problem i need to make a win98 boot disk, and i can't use my a: drive.  i put adisk in and nothing. i need to find and mount it. 
thanks!

---

### Post by jkeyes0 on 2007-05-10
I had to do this same thing last night.

Open a terminal (applications->accessories->terminal) and type:
```
sudo mount /dev/fd0
```

that should do the trick.

---

### Post by Najand on 2007-05-10
> **jkeyes0 said:**
> I had to do this same thing last night.

Open a terminal (applications->accessories->terminal) and type:
```
sudo mount /dev/fd0
```

that should do the trick.

Actually it won't do the trick if he/she hasn't it defined under his/her fstab file.

---

### Post by jkeyes0 on 2007-05-10
> **Najand said:**
> Actually it won't do the trick if he/she hasn't it defined under his/her fstab file.

A very good point. If the system was set up with a floppy drive installed, it should already be in the fstab file though, through autodetection.

---

### Post by orb9220 on 2007-05-10
Also check your bios that the floppy is enabled. And is in boot sequence?

For me anyway in windows if the floppy is not setup as first boot device then windows never sees it weird.

---

### Post by rickycodie on 2007-05-11
so i tried 
sudo mount /dev/fd0 
 and no worky. how do i find and mount it?

---

### Post by totalnub on 2007-05-11
ok, well you need to create a mountpoint:
```
sudo mkdir /media/*whatever*
```
then:
```
sudo mount /dev/fd0 /media/*whatever*
```

---

