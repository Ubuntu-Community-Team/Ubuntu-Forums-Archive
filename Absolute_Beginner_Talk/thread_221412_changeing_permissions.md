---
title: "changeing permissions"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-07-23
how do i change permissions from lex1 to admin in the directory below
i tried chown -r /etc/suck but got -r invaild option

total 24
drwxrwxrwx 2 news news 4096 2006-07-22 08:59 .
drwxr-xr-x 90 root root 4096 2006-07-22 12:35 ..
-rw-rw-r-- 1 news news 1946 2004-10-27 13:37 get-news.conf
-rw-rw-r-- 1 news news 56 2004-10-27 13:37 suckkillfile
-rw-r--r-- 1 lex1 lex1 463 2006-07-22 08:55 sucknewsrc
-rwxrwxrwx 1 news news 122 2006-07-05 11:15 sucknewsrc.old


lex1

---

### Post by scxtt on 2006-07-23
use -R ...

(brought to you by the chown manpage)

---

### Post by lex1 on 2006-07-23
thanks for your post

at the moment suck looks like this

drwxrwxrwx  2 admin admin 4096 2006-07-23 09:59 .
drwxr-xr-x 90 root  root  4096 2006-07-23 08:18 ..
-rw-rw-r--  1 admin admin 1946 2004-10-27 13:37 get-news.conf
-rw-rw-r--  1 admin admin   56 2004-10-27 13:37 suckkillfile
-rwxrwxrwx  1 admin admin  463 2006-07-22 08:55 sucknewsrc
-rwxrwxrwx  1 admin admin  122 2006-07-05 11:15 sucknewsrc.old


how to change it so it looks like this:
with news and new permissions

drwxrwxrwx 2 news news 4096 2006-07-22 08:59 .
drwxr-xr-x 90 root root 4096 2006-07-22 12:35 ..
-rw-rw-r-- 1 news news 1946 2004-10-27 13:37 get-news.conf
-rw-rw-r-- 1 news news 56 2004-10-27 13:37 suckkillfile
-rw-r--r-- 1 admin admin 463 2006-07-22 08:55 sucknewsrc
-rwxrwxrwx 1 news news 122 2006-07-05 11:15 sucknewsrc.old


thanks 

lex1

---

### Post by Indras on 2006-07-23
> **lex1 said:**
> thanks for your post

at the moment suck looks like this

drwxrwxrwx  2 admin admin 4096 2006-07-23 09:59 .
drwxr-xr-x 90 root  root  4096 2006-07-23 08:18 ..
-rw-rw-r--  1 admin admin 1946 2004-10-27 13:37 get-news.conf
-rw-rw-r--  1 admin admin   56 2004-10-27 13:37 suckkillfile
-rwxrwxrwx  1 admin admin  463 2006-07-22 08:55 sucknewsrc
-rwxrwxrwx  1 admin admin  122 2006-07-05 11:15 sucknewsrc.old


how to change it so it looks like this:
with news and new permissions

drwxrwxrwx 2 news news 4096 2006-07-22 08:59 .
drwxr-xr-x 90 root root 4096 2006-07-22 12:35 ..
-rw-rw-r-- 1 news news 1946 2004-10-27 13:37 get-news.conf
-rw-rw-r-- 1 news news 56 2004-10-27 13:37 suckkillfile
-rw-r--r-- 1 admin admin 463 2006-07-22 08:55 sucknewsrc
-rwxrwxrwx 1 news news 122 2006-07-05 11:15 sucknewsrc.old


thanks 

lex1

For things like this, it's quickest to use the octal equivalent of the permission you want to set, like this:

```
chmod 644 sucknewsrc
```

Here's a decent explanation of octal values I just googled up:

[http://www.ss64.com/bash/chmod.html](http://www.ss64.com/bash/chmod.html)

---

### Post by lex1 on 2006-07-23
thanks for your post 

i used chmod644 and it did change sucknewsrc

but how to change from admin to news 

drwxrwxrwx  2 admin admin 4096 2006-07-23 09:59
-rw-rw-r--  1 admin admin 1946 2004-10-27 13:37 
-rw-rw-r--  1 admin admin   56 2004-10-27 13:37 suckkillfile
-rwxrwxrwx  1 admin admin  122 2006-07-05 11:15 sucknewsrc.old





these lines  should be news

lex1

---

### Post by Indras on 2006-07-23
Easy!

```
chown news:news sucnewsrc
```

---

### Post by catlett on 2006-07-23
To change group ownership use chgrp
```
sudo chgrp system_groupname /location_of_files_or_folders
```
Or in your case 
```
sudo chgrp news /etc/suck
```

To change files amd folder ownership use chown
```
sudo chown system_username /location_of_files_or_folders
```

To change permissions you can also use Nautilus. Browse to the file or folder and right-click to get the option menu. Select Properties. Then select the Permissions tab. You can then check off the permissions you want it to have. If root owns the file and the user you are logged in with can't change the permissions, then launch Nautilus as root and then browse to the file/folder and make the changes in the Permission tab. Launch nautilus as root with this command ```
gksudo nautilus
```

---

