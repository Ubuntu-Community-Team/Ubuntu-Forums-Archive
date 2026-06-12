---
title: "Running install script?"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by meniscus on 2007-01-15
Im trying to install matlab and the readme file in the cd just saya its simply a case of running a script called "INSTALL" as root
 
I got the following.


```
meniscus@meniscot:/media/cdrom0$ sudo ./INSTALL
sudo: unable to execute ./INSTALL: Permission denied
meniscus@meniscot:/media/cdrom0$ ./INSTALL
bash: ./INSTALL: /bin/sh: bad interpreter: Permission denied



```

Am i doing some thin silly?

---

### Post by Pobega on 2007-01-15
Files called INSTALL are usually documentation. Most likely you have to do
> ./configure
make
sudo make install
If install actually *is* a script, though, try this:
> chmod +x INSTALL
sudo ./INSTALL

---

### Post by meniscus on 2007-01-15
Its def a script alright. I did that and got this!

```

meniscus@meniscot:/media/cdrom0$ sudo chmod +x INSTALL
chmod: changing permissions of `INSTALL': Read-only file system
meniscus@meniscot:/media/cdrom0$ sudo ./INSTALL
sudo: unable to execute ./INSTALL: Permission denied
meniscus@meniscot:/media/cdrom0$


```

---

### Post by zerhacke on 2007-01-15
Seems to me that your script is on a CD, which is a read only medium, therefore cannot change the permissions on it.  Try copying the whole kit and kaboodle to your home directory, change the permissions then, and run the script again.

---

### Post by meniscus on 2007-01-15
thanks. that did it!

---

