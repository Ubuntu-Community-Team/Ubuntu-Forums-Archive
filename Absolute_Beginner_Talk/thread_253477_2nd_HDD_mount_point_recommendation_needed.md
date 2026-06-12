---
title: "2nd HDD mount point recommendation needed"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by ajifans on 2006-09-08
Hi, I currently have three partitions:

1) mounted at swap
2) mounted at /
3) mounted at /home

With a 2nd hard drive, what would you set the mount point at if you simply wanted to use it as spare home storage?

I'm thinking of setting it as /home/spare and then using gksudo-nautilus to set me as the owner, which would allow me to use it wihout root privledges.  Any problems with this?

---

### Post by infoburner on 2006-09-08
if the new hdd is going to belong to you anyway, why not just put it in your home directory?
like: /home/*username*/spare

---

### Post by kanem on 2006-09-08
I used to mount extra storage partitions to folders in my home directory but now I just mount them to /mnt and make a link to ithem in my home directory. Two small benefits of this are: if you mount directly to your home, that partition can be deleted fairly easily, whereas an erased link is of no big importance. And, in the case of mounting to folders in your home directory, Nautilus did this weird thing where if you click and drag just a little the folder that the partition is mounted to, Nautilus will try to copy all the contents of that partition to the parent folder.

---

### Post by StickyStyle on 2006-09-08
It would work perfectly fine to put the drives mount point there.  
A nit-pick though would be that directories under /home are generally reserved for users home folders, so if you for some wild reason wanted to create a user called 'spare' /home/spare would be it's home folder by default.  Although this can be changed for that user fairly easily.

Myself i would make another directory off of /, call it /spare and mount the drive there still changing the ownership.   Or perhaps you want the drive only for yourself, mount it under 
/home/your username/spare <- that may acually be what you are looking for.

---

