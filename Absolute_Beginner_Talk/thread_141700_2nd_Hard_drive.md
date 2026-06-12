---
title: "2nd Hard drive"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by evilc on 2006-03-08
I installed Ubuntu on new hard drive (removed original one with Winxp as I didn't want to dual boot). Now after 2 days using linux I have ditched XP and set the HD as slave, partitioned it as ext3 and it shows up in system/disk as hdb. In Nautilus I can see it in /dev/hdb, my question is how do I get it to mount on startup so that I can use it (same as hda).  Thanks

---

### Post by evilgold on 2006-03-08
to have it mount automatically you just need to add it to fstab.

since i'm too distracted to explain it now i will simply say

man fstab
(enter that in a terminal)

Someone else will probably come and tell you exactly what to do, but the fstab man is all you should need

---

### Post by andrewsawyer on 2006-03-08
You have to edit the /etc/fstab file.  Do it from terminal by typing 'sudo gedit /etc/fstab'.

You need to enter a new line that should look as follows:
```
/dev/hdb1      /media/drive2     ext3   defaults   0 0
```

You will also need to create a directory called /media/drive2.  Do this by typing:

```
sudo mkdir /media/drive2
```

It should now mount on each boot.  I have assumed that the partition you have formatted on hdb is partition 1 (hdb1).

On a side note: Yeah!!! 400th post.

---

### Post by deBaas on 2006-03-08
[QUOTE=evilc]I installed Ubuntu on new hard drive (removed original one with Winxp as I didn't want to dual boot). Now after 2 days using linux I have ditched XP and set the HD as slave, partitioned it as ext3 and it shows up in system/disk as hdb. In Nautilus I can see it in /dev/hdb, my question is how do I get it to mount on startup so that I can use it (same as hda).  Thanks[/QUOTE]
A nice way to use two disks is one small for ubuntu and the large for swap and /home. Thats the place where I am always short of disk space.

---

### Post by evilc on 2006-03-08
Thanks Andrewsawyer only one more ? How can I change the permissions for this drive to make it for all users.  deBaas Yup your right will be using it for swap and home when I can figure out how to do it.

---

### Post by djlosch on 2006-03-11
what do u mean usable by all users?

i figure u want it just as like some storage space.  if u have it mounted as like /archive, and want all users to be able to read only, type:
sudo chown root /archive -R
sudo chgrp root /archive -R
sudo chmod 755 /archive -R

the first line is making the user root own everything in /archive and recursively down
the 2nd line is makeing the group root own everything in /archive and recursively down
the 3rd line is making it so everyone has read and execute access, but only root has write access

if you want one big folder called /archive that everyone can write in, do this:
sudo chgrp users /archive -R
sudo chmod 775 /archive -R

then make sure everyone that u want to have write access is in the group users.  they will all have write access.


i HIGHLY recommend doing the first method.  whenever i download stuff, i download it to ~/download and when it gets completed it moves to ~/completed.  then i look thru it and make sure it's ok, clean the file names/tags if necessary, and then sudo mv the file to my /mnt/archive drive.  this drive has 1 partition and is solely mp3s, install files, movies, and all that jazz.  this way, in the event that the system gets compromised, your user only has read access to your files.  also, should the machine go down, you dont have to worry about home or the files no one specifically owns.

---

