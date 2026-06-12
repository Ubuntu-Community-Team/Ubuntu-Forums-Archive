---
title: "How do I format and use an external harddrive?"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by neocookie on 2008-04-12
I've bought an external harddrive case (USB2) for a new-ish 80gig drive I've ripped out of an old PC running ubuntu. 

I've split it into 2 partitions using gparted (media, svn) and formatted each using:

```
sudo mke2fs -j -m 0 /dev/sdaX
```

The partition and format was successful... however I can't get write access to the disks as the normal user.

Any ideas how I might solve this?

---

### Post by joshrobinson on 2008-04-12
what filesystem are you using?
how are you mounting it?

---

### Post by GreenB on 2008-04-12
first i would change the owner by 
```

sudo chown _User  /media/_Harddrive

```
where _User_ is the new owner, and /media/_Harddrive are the location and name of your hard drive.
then you might wanna use a chmod to give the proper read write permissions.
[

---

### Post by neocookie on 2008-04-13
OK, I've chowned the drives...
```

~$ sudo chown -Rf phill.phill /media/disk
~$ ls -alh /media/disk
total 24K
drwxr-xr-x 3 phill phill 4.0K 2008-04-12 10:20 .
drwxr-xr-x 5 root  root  4.0K 2008-04-13 09:18 ..
drwx------ 2 phill phill  16K 2008-04-12 10:20 lost+found

```

Now I can access the drives and make directories/files on the command line, but nautilus still won't let me create/move/delete files from the GUI.

Whats next? :(

---

### Post by Michael.Godawski on 2008-04-13
And when you run nautilus with superuser privileges? This might be dangerous because you can easily delete something important. But you can test it.

```
gksudo nautilus
```

---

### Post by neocookie on 2008-04-14
Yep, that lets me do what I want. But as you say, I can't operate like that all the time.

Next?

---

### Post by logos34 on 2008-04-14
sudo chown -R phil:phil /media/disk
sudo chmod -R 755 /media/disk

---

