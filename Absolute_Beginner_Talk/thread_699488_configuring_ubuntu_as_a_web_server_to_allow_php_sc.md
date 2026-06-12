---
title: "configuring ubuntu as a web server to allow php scripts to make folders"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Corrupter on 2008-02-17
Hey guys, suffice to say, i did in fact search quite vigorously through the forums to find my answer, and got a large part of that answer already but there is still a bit im needing to clear up, so please bare with me.

I successfully made a LAMP server and it is server a PHP forum quite well, however any time that forum needs to make new directories and alter permissions for files (CHMOD) it fails to do so and im forced to manually make those changes.  I cant seem to find the section where i would change and enable those permissions for the php files running on the server.

I must admit that my experience is limited although atleast i know how to get around in Ubuntu without setting it on fire =P  Be gentle.

---

### Post by bilge.tutak on 2008-02-17
Did you adjust the permissions/group/owner of the parent folder where the folders will be created? The parent folder should permit the web user to create folders. Please check the permissions/group/owner of the parent folder.

---

### Post by Origin415 on 2008-02-17
```
sudo chown -R www-data */path/to/site's/root/*
```

---

### Post by samb0057 on 2008-02-17
You have to give the "www" user (the user that apache runs under) write permissions to the parent directory you want to create directories in.

You can do this two ways:
Allow all users to write to the directory
```
chmod 777 directory
```

Make the www user the owner of the directory.
```
chown www directory
```

Then you can use mkdir() or any other file/directory creation functions freely in your php scripts (for the directory you just made writeable).

---

### Post by Corrupter on 2008-02-17
funny thing is, i did actually try to chown as www-data and also tried to set the permissions to 777, it still doesnt seem to be working, perhaps i'll try to reset them and do it again.

is it www or www-data?  i tried www-data i'll give www a try.

---

