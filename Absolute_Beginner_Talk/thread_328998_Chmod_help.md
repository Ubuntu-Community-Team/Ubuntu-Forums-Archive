---
title: "Chmod help"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by ironfistchamp on 2006-12-31
Hey all

Just wondering how to use chmod properly. I want to add write permissions for one other user but don't have a clue how to do this. I can only access through the terminal so no nice GUI to do it.

Any help would be great.

Thanks

Ironfistchamp

---

### Post by taurus on 2006-12-31
Which directory do you plan to change the permission?

---

### Post by ironfistchamp on 2006-12-31
/var/www   i have sudo permissions but there are a couple of html files I want to have my reg user able to write to. This is on a friends server that is always online so I can host a website.

---

### Post by taurus on 2006-12-31
You mean something like

```
sudo chmod -R 777 /var/www
```
Then, everybody can read, write, and delete stuff in /var/www!!!

---

### Post by ironfistchamp on 2006-12-31
Yeah something like that but for a specific user. So not everyone can read/write/delete but just this one person I name. How could I do that?

---

### Post by FredSambo on 2006-12-31
try 

```
chown nameofuser.nameofgroup nameoffile
```

---

### Post by taurus on 2006-12-31
Then you need to add that user to the group that owns /var/www, hopefully not root!!!  So, what's the output of this command from a terminal?

```
ls -la /var/www
```

---

### Post by ironfistchamp on 2006-12-31
```

drwxr-xr-x 11 varuser patrick  4096 2006-12-31 23:31 .
drwxr-xr-x 17 root    root     4096 2006-12-14 12:10 ..
-rwxr-xr-x  1 varuser patrick  2121 2006-02-15 13:04 access_admin.php
-rwxr-xr-x  1 varuser patrick  4656 2006-03-30 13:43 admin.php
-rwxr-xr-x  1 varuser patrick 10843 2006-09-08 11:39 category.php
drwxrwxrwx  2 varuser patrick  4096 2005-05-20 12:03 cfg
-rwxr-xr-x  1 varuser patrick   733 2005-10-03 17:19 checklogin.php
drwxr-xr-x  2 varuser patrick  4096 2005-04-29 10:22 extra
drwxr-xr-x  2 varuser patrick  4096 2006-02-16 11:42 images
drwxr-xr-x  4 varuser patrick  4096 2006-02-16 12:00 includes
-rwxr-xr-x  1 varuser patrick  6885 2006-10-27 10:26 index.php
drwxr-xr-x  2 varuser patrick  4096 2006-02-16 12:24 languages
-rwxr-xr-x  1 varuser patrick 14590 2006-09-08 12:18 products.php
drwxrwxrwx  2 varuser patrick  4096 2006-12-18 12:46 products_pictures
-rw-r--r--  1 varuser patrick   390 2005-11-04 13:52 README.txt
drwxr-xr-x  4 varuser patrick  4096 2005-09-08 09:22 smarty
-rwxr-xr-x  1 varuser varuser  2438 2006-12-31 23:35 style1.css
drwxrwxrwx  3 varuser patrick  4096 2005-04-29 10:22 templates
drwxrwxrwx  2 varuser patrick  4096 2006-12-31 23:38 templates_c


```

That is the output I get.

---

### Post by taurus on 2006-12-31
So **varuser** is the owner and **patrick** the groups then...  Just add your friend's username to group patrick in /etc/group

```
sudo nano -w /etc/group
```
and change the permission to /var/www with

```
sudo chmod -R 775 /var/www
```
Now, varuser and everybody in group patrick can read and write (also delete) to /var/www!

---

### Post by ironfistchamp on 2006-12-31
Thanks will try this tomorrow. Ironfistchamp

---

