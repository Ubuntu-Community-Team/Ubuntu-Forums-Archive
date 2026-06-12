---
title: "Do you have a group called 'nobody' in your system?"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-03-13
cat /etc/passwd |grep nobody
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh

passwd seems to indicate that user 'nobody' is in group 'nobody'.

However, when I 'cat /etc/group', there isn't any 'nobody' group.

Is that the way it is suppose to be?

Thanks !

---

### Post by RJMacReady on 2006-03-13
Lol, what fun could be had.

Nobody's Home.

---

### Post by jrib on 2006-03-13
I have that too if that makes you feel a little less suspicious.  No idea what it is for

---

### Post by stuporglue on 2006-03-13
I remember I was supposed to use nobody::nogroup when I followed some tftp tutorial trying to get a box to PXE boot. So, I think it IS supposed to be there...don't know why though.

---

### Post by Zimmer on 2006-03-13
[http://www.debianhelp.co.uk/usersid.htm](http://www.debianhelp.co.uk/usersid.htm)

[http://linuxgazette.net/issue61/ward.html](http://linuxgazette.net/issue61/ward.html)

will give you comfort that the nobody user is usually required to run processes without having privileges..
But I must admit I need to read further to understand this properly.

---

### Post by taurus on 2006-03-13
I believe you need "nobody" and "nogroup" if you plan to set up an ftp server...

[QUOTE=RJMacReady]Lol, what fun could be had.

Nobody's Home.[/QUOTE]
I am nobody!!!  :p

---

### Post by matthew on 2006-03-13
From this page under topic 8.1.1 
[http://www.debian.org/doc/manuals/system-administrator/ch-sysadmin-users.html](http://www.debian.org/doc/manuals/system-administrator/ch-sysadmin-users.html)

>  UID 65534 is user "nobody", an account with no rights or permissions.  


---

### Post by Kurt` on 2006-03-13
Certain services, Apache web server for instance, run as the 'nobody' user. :)

---

### Post by Tipo on 2006-03-13
> 
UID 65534 is user "nobody", an account with no rights or permissions. 

Aww. No rights... No equality here, poor Nobody...:p

---

