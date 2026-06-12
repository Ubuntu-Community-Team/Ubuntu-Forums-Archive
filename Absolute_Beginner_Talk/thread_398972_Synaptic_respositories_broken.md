---
title: "Synaptic respositories broken"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by petroleumjelliffe on 2007-04-01
I tried adding a repository but I typed it in wrong, and sources.list got screwed up.

```
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
ftp://ftp.videolan.org/pub/videolan/ubuntu
ftp://ftp.videolan.org/pub/videolan/ubuntu
deb ftp://ftp.videolan.org/pub/videolan/ubuntu dapper universe
```

I opened up sources.list, deleted the last three lines, but i can't save it.

I saw this [forum post]("http://www.ubuntuforums.org/showthread.php?p=2377929#post2377929") where it said to run 

```
gksudo gedit /etc/apt/sources.list
```

but I get an error message in Terminal that says "sudo: gedit: command not found."

I'm running xubuntu alternate.  How do I fix sources.list?  Synaptic doesn't show anything now.

---

### Post by Maestro23 on 2007-04-01
gedit is the gnome text editor.  You need to install it.

> sudo aptitude install gedit

I use nano also.

> sudo aptitude install nano

---

### Post by petroleumjelliffe on 2007-04-01
I can't install anything because the sources.list file is screwed up.

Is there another way to edit save save changes to sources.list?

---

### Post by zvacet on 2007-04-01
[http://doc.gwos.org/index.php/Nautilus_Scripts]("http://doc.gwos.org/index.php/Nautilus_Scripts")

Install first two scripts.To edit source list you have to be administrator,not a common user.Only administrator have privileges to change,install.....and so on.But maybe will be good to do 
```
sudo aptitude update
``` 
and 
```
sudo aptitude upgrade
```

before you start anything.if you run it to the problems just say so.Somebody will help you.

---

### Post by Maestro23 on 2007-04-01
> **petroleumjelliffe said:**
> I can't install anything because the sources.list file is screwed up.

Is there another way to edit save save changes to sources.list?

Try:

sudo mousepad....

I believe that is the default text editor for Xubuntu. Try to edit the file with that.

---

### Post by NeoLithium on 2007-04-01
Try typing:
```

sudo nano -w /etc/apt/sources.list

```
It's a terminal based editor that should allow you to delete the lines and save the new sources list :)

---

### Post by petroleumjelliffe on 2007-04-01
@neoLithium
That worked!  I knew i had to use sudo somehow to gain write priviledges, but didn't know of what the terminal based text editor was.

---

