---
title: "apache help"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by grim918 on 2005-11-19
im new to linux and i just installed apache but im having trouble with the linux file system. in windows the default folder for storing your web pages is called htdocs but in linux i cant find the folder. can someone help me out and tell me where to find the folder so i can put up my webpages. thanks to anyone that can help me out.

---

### Post by [Rui] on 2005-11-19
Possible spots: /srv/www/ or /var/www/ or more...

---

### Post by zhorty on 2005-11-19
Hi.
The dir is actually /var/www/apache2-default

but just forget that, it's permission on it etc, etc.
Do this:
```
sudo su
```
Type your root pw
```
gedit etc/apache2/apache2.conf
```
Search for "group" and find thist text:
```
User X
Group X
```
Edit "X" to your ubuntu username and groupname (the groupname is often the same as the username)

Save the file.

Now, do this:
```
mkdir /home/yourusername/www
```
```
gedit etc/apache2/sites-enabled/default
```
Edit to example:
```
DocumentRoot /home/yourusername/www
```
```
<Directory /home/yourusername/www
```

Now, find the line starting with RedirectMatch XXXX.
Edit the line to
```
# RedirectMatch XXXX
```
With other words, just set a # at the start at the line.

Save the file.

Restart the apache server:
```
/usr/sbin/apache2ctl restart
```

Now, the default www dir should be /home/yourusername/www

---

### Post by BenPimpin on 2005-11-19
After typing

```
gedit etc/apache2/apache2.conf
```

I get

> (gedit:16755): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Any ideas would be appreciated.

---

### Post by BenPimpin on 2005-11-19
After I type

```
gedit etc/apache2/apache2.conf
```

I get

> (gedit:17014): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Appears to be some kind of gedit problem and it only happens when I'm logged in as root.
Any ideas would be appreciated.

---

### Post by estel on 2005-11-19
If I open gedit as root I do get that error, but I also get gedit so I don't worry about it.

The web directory is actually *just* /var/www. But because of permissions, you won't be able to save anything in there.

The easier solution (rather than the above making your Home directory into the new server root) is to:
```
sudo chown -R YOURNAME /var/www
```
To make sure that you own the folder...
```
chmod -R 755 /var/www
```

---

### Post by zhorty on 2005-11-20
go for nano then.
Should works well in root

nano etc/apache2/apache2.conf

---

