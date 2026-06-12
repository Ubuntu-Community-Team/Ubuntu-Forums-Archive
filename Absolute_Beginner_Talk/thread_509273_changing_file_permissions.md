---
title: "changing file permissions"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Harry789 on 2007-07-25
I have a separate 80 Gb HD that I connect via USB. It is formatted ext3.

Ubuntu mounts it just fine, but i realize that the files are protected with user rights from my former installation (Mandriva).

I would like to "unlock" all files so they are available to all users regardless of who mounts the drive. I am speaking all of it - subfolders too.

I have tried to play around with

$ sudo chmod 777 /media/disk (the 80 gb mounts as "disk")

but it does not always seem to want to work. It will change the folders but not the files.

How do I go about that?

---

### Post by sumguy231 on 2007-07-25
I believe that if you want that to be recursive it needs to be:
$ sudo chmod -R 777 /media/disk
By the way, it's handy to know that for some reason chmod, chown, and chgrp all use a capital R for recursive for some weird reason.

---

### Post by jd65pl on 2007-07-25
> **sumguy231 said:**
> I believe that if you want that to be recursive it needs to be:
$ sudo chmod -R 777 /media/disk
By the way, it's handy to know that for some reason chmod, chown, and chgrp all use a capital R for recursive for some weird reason.


Because lower case "r" is the option for read only i.e.

chmod -rwx

---

### Post by asmoore82 on 2007-07-25
777 with make all files executable on that disk....
while this is really just a housekeeping issue and not something really serious, a cleaner way to do this would be using chmod's lettered permission mode ...
```
~ $ sudo chmod -R o+rw /media/disk
```
this will give read/write to everyone without making file executable that don't need to be and without removing executable from directories which is neccessary if you want to browse through the filesystem.

---

### Post by Carlos Santiago on 2007-07-25
I believe the problem is the user ID because the first user ID in Ubuntu 
is user 1001 while in others distros is 500.

Change the user of all the data on your disk with:
```
sudo chown -R your_user:your_user /media/your_drive
```

---

### Post by Harry789 on 2007-07-25
thanx Carlos and all others,

I will try this, and report back if I experience more trouble.

---

### Post by sumguy231 on 2007-07-25
> Because lower case "r" is the option for read only i.e.
Yeah, but it seems to me that all other GNU utils use lowercase r for recursive, and read-only just as easily could have been uppercase. Not that it matters.

---

