---
title: "question about ownership of files"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by edwin_ancaer on 2007-05-30
I seem to have a problem with ownership of files. 

I cannot read the files in /var/www, which is the root directory for apache, when logged in as user edwin. This user is part of the group www-data. 

Even the command ls seems not to work  

edwin@Ottopedi:~$ ls -l /var/www
total 0
?--------- ? ? ? ?                ? /var/www/ajax-test.html
?--------- ? ? ? ?                ? /var/www/ajax-testx.html
?--------- ? ? ? ?                ? /var/www/atf.html
?--------- ? ? ? ?                ? /var/www/index.html

When logged in as root, ls displays the following: 

root@Ottopedi:/home/edwin# ls -l /var/www
total 20
-rw-r--r-- 1 www-data www-data 1158 2006-12-01 22:18 ajax-test.html
-rw-r--r-- 1 edwin    www-data 1158 2007-05-30 21:25 ajax-testx.html
-rw-r--r-- 1 www-data www-data   28 2006-11-30 21:41 atf.html
-rw-rw-r-- 1 www-data www-data 5258 2006-11-23 22:57 index.html

I thought this indicates that everyone can read the files in /var/www.

What mistake am I making? 

thanks in advance

---

### Post by bernied on 2007-05-30
Not sure if this will go anywhere, but what are the permissions on the directory /var/www ?
```
sudo ls /var | grep www
```or```
sudo ls -al /var/www
```and look for the . entry.

---

### Post by lambros on 2007-05-30
It would be interesting to know what the permissions are on the /var/www/ folder itself.  Please could you post the output of
```
ls -l /var/www
```

I'm not sure, but I'm guessing you might not have the right "execute" permissions and/or ownership for that folder.  In order to be able to list or view the contents of a folder, I believe you need "execute" privileges on it.

Lambros

---

### Post by edwin_ancaer on 2007-05-30
edwin@Ottopedi:~$ sudo ls -al /var/www
Password:
total 28
drw-r--r--  2 www-data www-data 4096 2007-05-30 21:25 .
drwxr-xr-x 15 root     root     4096 2006-11-23 22:57 ..
-rw-r--r--  1 www-data www-data 1158 2006-12-01 22:18 ajax-test.html
-rw-r--r--  1 edwin    www-data 1158 2007-05-30 21:25 ajax-testx.html
-rw-r--r--  1 www-data www-data   28 2006-11-30 21:41 atf.html
-rw-rw-r--  1 www-data www-data 5258 2006-11-23 22:57 index.html


By the way: where do i find an explication of the output of ls. I tried the manpage, but ther is only a list of all options, no explication of the meaning of the different columns. 

This may seem stupid questions, but I'm a mainframe programmer starting Linux, and directories aren't my speciality.

---

### Post by bernied on 2007-05-30
The group needs execute permission on the directory. Execute has a different meaning for a directory, as you have just discovered.
```
sudo chmod g+x /var/www
```should fix it.

---

### Post by edwin_ancaer on 2007-05-30
Another problem solved, 

thans very much. :)

---

### Post by bernied on 2007-05-30
No prob. Sorry I don't know the answer to your other question.
Something like:
type&permissions [depth] owner group size date time name
I made up [depth], it looks like if it's a normal file it's 1, if it's a directory with only files in it, it's 2, etc.
Google around for info on permissions - it does my head in too.

---

