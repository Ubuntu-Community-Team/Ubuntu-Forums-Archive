---
title: "whats my default mysql password ? default in ubuntu 7.04"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by mnewbegin on 2007-06-04
what is the default mysql password when you do the LAMP install with Ubuntu 7.04 Server?

I tried this command 

root@ubuntu:/home/mark# mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

and got this result.

so how do I change this password


also another N00b question


i have 2 identical drives and i need to mount my second drive that wasnt formatted / mounted


i tried a few commands but i got an error saying i had to tell the file system of the drive.

---

### Post by Cypher on 2007-06-04
There is no default password, just try
```

mysql -u root

```

---

### Post by Cypher on 2007-06-04
As far as mounting your un-formatted drive goes. You need to first format it using 'mkfs.ext3' and then 'mount' it. "man mkfs.ext3' and 'man mount' will give you all the details..:)

---

### Post by mnewbegin on 2007-06-04
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)


is the error with no password.

---

### Post by Cypher on 2007-06-04
OK..then just try
```

mysql

```

---

### Post by mnewbegin on 2007-06-04
same error.

what do i type to remove and reinstall it without messing up my system?

i dont really have much of anything configured yet, but it would be nice to not have to reinstall everything.


i used the base install LAMP server for ubuntu, im surprised i was having this problem

---

### Post by kvonb on 2007-06-04
It might be a firewall problem, did you install any firewall stuff?

Port 3306 needs to be open I believe.

It could also be a hostname problem, I've had that recently.  Check /etc/my.cnf and see if you have this line:

```
bind-address        = 127.0.0.1
```

If you gave it your computer's hostname on install, that could be the problem, and make sure that you have this in your /etc/hosts file:

```
127.0.0.1 localhost
```

Regards, Kev :)

.

---

### Post by kvonb on 2007-06-04
AHA!!

Someone is being a naughty boy!!

You are using the root system account, I'm sure that is banned by default.  Try logging in as a regular user and running mysql from there (no sudo).

---

### Post by mnewbegin on 2007-06-05
i dont seem to have a /etc/my.cnf

ERROR 1045 (28000): Access denied for user 'mark'@'localhost' (using password: NO)


is the error when i run with no root access.

thats the only user account on the system so is that still considered the root account?



127.0.0.1       localhost
192.168.0.129   ubuntu.lyncomail.com
 
inside hosts file

---

