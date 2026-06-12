---
title: "can't access original drive"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by normalc on 2006-09-18
Hay there
 I'm a first timer ,with ubuntu or linux.
have installed ubuntu with it's own patition,but i can't seam to read the original windows 2000 partition.it's displayed as Vfat
     

   a tad bit of advice would be appreciated.

---

### Post by hassan_saeed on 2006-09-19
A partition has to be in 'mounted' state to be read.

i think when you installed ubuntu you did not mention while partitioning wheather to mount your 2000 partition.

if you only want to view some data you can goto --> system---> administration--->disks and select your partiion and browse it. but the problem will be that if you copy any thing it will be owned by user: root and you will not be able veiw any content until you are logged in as root.

i know there *is* some procedure to make the drive appear on desktop and enable it. but dont know *how* it is done.
hope this gives you some idea

---

### Post by normalc on 2006-09-19
Thanks for the tid-bit ,  I,ve been through that part but alas...
I would like to access the data and don't know how to mount the other drive.

---

### Post by mokmoki on 2006-09-19
you might want to check [this]("http://www.psychocats.net/ubuntu/mountwindows") out...

---

### Post by Brunellus on 2006-09-19
> **normalc said:**
> Thanks for the tid-bit ,  I,ve been through that part but alas...
I would like to access the data and don't know how to mount the other drive.
if in GNOME (regular ubuntu):

go to System > Administration > Disks 

you will see a list of disks and partitions.  then you will have the option of mounting them.

---

