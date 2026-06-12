---
title: "chown of directory denied when using sudo?"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by crewfan on 2007-09-14
I'm trying to change the owner of my "/fulham" directory from root to another user but I get the following error.  Why is this operation not permitted?

drwxr-xr-x  2 root root  16K 1969-12-31 19:00 .
drwxr-xr-x 23 root root 4.0K 2007-09-04 15:16 ..
david@david-desktop:~$ sudo chown ubufileserv /fulham
Password:
chown: changing ownership of `/fulham': Operation not permitted

Many thanks!

---

### Post by alienexplorers on 2007-09-14
try sudo chown -hR username:username /directory

---

### Post by Tautoa on 2007-09-14
What type of filesystem is it?

---

### Post by crewfan on 2007-09-16
It's Fat32.  I'm trying to set up a samba share.  Thanks for you help!

---

### Post by Tautoa on 2007-09-16
Right, as far as I know, Fat32 doesn't support permissions on files, so that might explain why chown-ing it won't work?
If it was me, I would change it to an Ext3 partition, and use that program that lets Windows understand Ext3 (I can't remember the name, Ext3fs or something?)

Bearing in mind, if you do convert it to Ext3, you'll have to move all your files to another partition while you're converting it, or you'll lose them all. I don't mean to patronise you, but I thought I had better mention that, just in case :)

---

