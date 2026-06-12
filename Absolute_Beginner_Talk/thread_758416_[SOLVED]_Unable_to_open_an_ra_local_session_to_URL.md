---
title: "[SOLVED] Unable to open an ra_local session to URL"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by ben22 on 2008-04-18
Hi,

when trying to import to a repository called "myrepo" I get the following error:

```
root@ben-desktop:/home/svn/myrepo# svn import /home/svn/myrepo/ file:///home/ben/test  -m "initial import"
svn: Unable to open an ra_local session to URL
svn: Unable to open repository 'file:///home/ben/test'
```


```

 root@ben-desktop:/home/svn/myrepo# ls -l
total 28
drwxr-sr-x 2 root subversion 4096 2008-04-18 07:09 conf
drwxr-sr-x 2 root subversion 4096 2008-04-18 07:09 dav
drwxr-sr-x 5 root subversion 4096 2008-04-18 07:09 db
-r--r--r-- 1 root subversion    2 2008-04-18 07:09 format
drwxr-sr-x 2 root subversion 4096 2008-04-18 07:09 hooks
drwxr-sr-x 2 root subversion 4096 2008-04-18 07:09 locks
-rw-r--r-- 1 root subversion  229 2008-04-18 07:09 README.txt
```

I also changed the permissions, but it did not help

```
root@ben-desktop:/home/svn/myrepo# ls -l 
total 28
drwxrwsr-x 2 root subversion 4096 2008-04-18 07:09 conf
drwxrwsr-x 2 root subversion 4096 2008-04-18 07:09 dav
drwxrwsr-x 5 root subversion 4096 2008-04-18 07:09 db
-rwxrwxr-- 1 root subversion    2 2008-04-18 07:09 format
drwxrwsr-x 2 root subversion 4096 2008-04-18 07:09 hooks
drwxrwsr-x 2 root subversion 4096 2008-04-18 07:09 locks
-rwxrwxr-- 1 root subversion  229 2008-04-18 07:09 README.txt

```

The user ben belongs to the group:
```
subversion:x:1001:ben,www-data,root
```

Any help?

Thx,
Ben

---

### Post by ben22 on 2008-04-18
It must be:

import PATH URL - with being the URL the destination repository

```
root@ben-desktop:/home/svn/myrepo# svn import /home/ben/test file:///home/svn/myrepo//testfile  -m "initial import
```

---

