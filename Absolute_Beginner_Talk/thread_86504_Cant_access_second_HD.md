---
title: "Cant access second HD"
date: 2005-11-05
forum: Absolute Beginner Talk
---

### Post by wadesmart on 2005-11-05
11052005 0925 GMT-5

I installed Breezy but before doing so I backed up two directorys: /tempdir and /home. 

I have a second hard. I copied /tempdir to /dev/hdd2 and copied /home to /dev/hdd3. 

I mounted these as follows: media/HD/hdd2 and media/HD/hdd3. 

I was able to access hdd3 with my /home files but when I go to hdd2 it says empty. 

Here is some data: 
/dev/hdd2             981M  558M  374M  60% /media/HD/hdd2
/dev/hdd3             2.0G  633M  1.3G  34% /media/HD/hdd3
/dev/hdd4             995M  4.0K  995M   1% /media/HD/hdd4

hdd2 and 3 are both ext3. 
I do not understand why Im having trouble accessing this.

Wade

---

### Post by Cufishing on 2005-11-05
I had to go: Sys>Admin>Shared folder>Add. Then added my other drives, and everything turned out.

---

### Post by earobinson on 2005-11-05
System -> Administration -> Disks or sudo disks-admin
(there is a non gui way to do this to)

is the disk listed there, or in gparted if you have it installed?

---

### Post by wadesmart on 2005-11-05
11052005 1509 GMT-5

I used gParted to create the partition originally. When I go to media/HD/hdd2 it just says empty. But in gParted it says there is something there. 

Ill try the shared example. 

Wade

---

### Post by gord on 2005-11-05
you could give 'gpart' a go, just incase you managed to partition it to a strange filesystem by accident. gpart should be able to guess the type of filesystem.

---

### Post by wadesmart on 2005-11-05
11052005 1745 GMT-5

I tried the Disks link from System>Admin. On My second disk, size 20GB, it says: Partition 2, device /dev/hdd2, filesystem Extended 3, Access path = none. Size is 996.22 MiB (Free space not available).  Same for hdd3; extended 3, no access path, 1.95 GiB (free space not available. 

I just mounted hdd2 at /media/HD/hdd2 and now it says that this is the access path and that 373.06 MiB Free in Size. Status is Accessible. 

I hit browse and nothing is there. 

Wait....I just selected Show Hidden files and there is one file: .Trash-root. 

OH MY Gosh! All my files are in that .Trash-root! 

YEA!!!! I have my data back. 

Ok. Why did that happen? 

Thanks for the help guys.

Wade

---

