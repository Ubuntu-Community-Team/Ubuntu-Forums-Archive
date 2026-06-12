---
title: "Urgent help on My External hard disk Please"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by nlbs on 2007-07-19
Hi!
I've a 40 GB external Hard disk , I've made two partitions on it  aFAt32 of 5 GB and the rest is EXT2
Everything was going fine and as teh fat one had a Drive name "SHARE" it was mounting it on 
/media/SHARE
and as the
EXT2 has no Drive name (I donno is how to set drive name on EXT2 partition Is there any option in Gparted to do this ?? I didnt find anything like that) It was mounting it on /media/disk
I was trying to set a different Mount Point  So I right Clicked and went to [Volume Tab] 
and Changed the Mount Point to 
/media/LinHD
then I reconnected the external Hard disk after unmounting
and Now It is Firing this Error 
[[IMG]http://img410.imageshack.us/img410/4273/picek9.th.png[/IMG]](http://img410.imageshack.us/my.php?image=picek9.png)
what Can I do to fix this
Plaese help Its my only back up disk.

---

### Post by jombeewoof on 2007-07-19
did you create /media/LinHD

and if you did, what permissions did you give it?
also did you update /etc/fstab

---

### Post by nlbs on 2007-07-19
Ya I've created it
and Its permission is```
drwxr-xr-x  2 root root  4096 2007-07-19 12:15 LinHD
```
Its still showing the same Error
And also I dont thinmk that I need to create that Directory cause I am not mounting manually its automount. It should create teh Directory by itself

---

### Post by jombeewoof on 2007-07-19
try this
```
 mount /dev/sda2 /media/LinHD 
```

that should at least get it mounted

---

### Post by nlbs on 2007-07-19
Ya Of cource it will work in this Way
but I am talking about problem on aotomounting.
It must have an way to face that error in a different way.
Whats teh File where it stores all the MountPoints
I think Its not /etc/fstab as its an external Hard drive Not fixed.

---

### Post by nlbs on 2007-07-19
I've fixed it by myself 
The Mount Point should be
LinHD
Instead of /media/LinHD
Thanks.

---

