---
title: "Cannot update programs from repositories"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by sheldoncwinn on 2006-12-25
I am running edgy. When I run the update manager I get the following error for each package that I am trying to update....

W: Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/tcl8.5_8.5.0-2~neto1-3v1ubuntu0_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/tcl8.5_8.5.0-2~neto1-3v1ubuntu0_i386.deb)
  The HTTP server sent an invalid reply header

I suspect that my headers got messed up when trying to install Flash9... but I do not know how to reset them... help!!

Thanks and merry christmas!

---

### Post by taurus on 2006-12-25
You can either edit /etc/apt/sources.list and place a # in front (to comment it out) of [http://3v1n0.tuxfamily.org/](http://3v1n0.tuxfamily.org/) or you can paste the output of your /etc/apt/sources.list here if you want...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
-or-
cat /etc/apt/sources.list
```

---

### Post by dbbolton on 2006-12-25
edit: never mind

---

### Post by sheldoncwinn on 2006-12-25
How do I edit the source list? Remember I am a newbie... Thanks for the answer!

---

### Post by taurus on 2006-12-25
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
Save the change and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by sheldoncwinn on 2006-12-25
I tried to go to thew terminal and type "edit/etc/sources.list" but I got the message "no write permission" ... what gives?

---

### Post by taurus on 2006-12-25
It's

```
**[COLOR="Blue"]gksudo gedit /etc/apt/sources.list[/COLOR]**
```

---

### Post by sheldoncwinn on 2006-12-25
It now shows no updates... as I thought that it should!! Thanks for the help! I have been running Edgy (on a dare) for about 2 weeks. I LOVE computing again.. and I do NOT understand why Windows exists.

This is really great. Thanks and merry Christmas.

---

### Post by taurus on 2006-12-25
Let's have a look at your /etc/apt/sources.list.  Paste the output of this command here.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

