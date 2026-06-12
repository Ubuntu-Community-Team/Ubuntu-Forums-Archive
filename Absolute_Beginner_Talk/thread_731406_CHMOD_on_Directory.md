---
title: "CHMOD on Directory"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by Frank_F on 2008-03-21
Hello

When I attempt to chmod 755 on  directory /media/external_drive_name/  and press enter, I dont receive an error message, yet the permissions to dont change from 700 ?

I su to root and still receive no success.


Thanks

---

### Post by wormser on 2008-03-21
Have you tried the -R (recursive) switch?

```
chmod ### -R /path/to/dir
```

---

### Post by unutbu on 2008-03-21
I think this has to do with the permissions on /media:

```

$ ls -ld /media
drwxr-xr-x 5 root root 4096 2008-03-21 21:34 /media
```

According to [http://www.albany.edu/faculty/gms/homepage101/unix_permissions.html#directory](http://www.albany.edu/faculty/gms/homepage101/unix_permissions.html#directory)
Group and Other do not have permission to create/delete files in the directory.
Subdirectories of /media can not give write permission to Group or Other either, since that would mean someone in say Group could create a directory in a directory of /media. In other words, the permissions are inherited as you go down the directory tree.

---

### Post by unutbu on 2008-03-21
Oops, I'm sorry. I have to eat my words.
You were trying to change from 700 to 755, and I don't see why that isn't permitted.
Please ignore my previous post.

---

### Post by unutbu on 2008-03-21
What happens when you do the following:

```
cd /media
sudo mkdir -m700 test
ls -ld /media/test

sudo chmod 755 test
ls -ld /media/test

```

---

