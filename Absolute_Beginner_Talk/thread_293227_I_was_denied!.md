---
title: "I was denied!"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by OptimusPrime on 2006-11-04
I can't remember how to edit the sources.list.  I get this:

wesley@wesley-laptop:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied

---

### Post by k|d&lt;FuNkY&gt;FrY on 2006-11-04
sudo gedit /etc/apt/sources.list

   -- or --

sudo nano /etc/apt/sources.list

---

### Post by bukwirm on 2006-11-04
Use sudo and a text editor : "sudo gedit /etc/apt/sources.list"

Ah! k|d<FuNkY>FrY beat me to the "Post" button by seconds!

---

### Post by taurus on 2006-11-04
> **k|d<FuNkY>FrY said:**
> sudo gedit /etc/apt/sources.list

   -- or --

sudo nano /etc/apt/sources.list

Actually,

```
gksudo gedit /etc/apt/sources.list
-or-
sudo nano -Bw /etc/apt/sources.list
```

---

### Post by CatKiller on 2006-11-04
You'll need an editor to actually edit that file. Like **gedit** or **nano** or whatever. And you'll need to edit it as root if you want to be able to actually save it.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by OptimusPrime on 2006-11-04
Thank you, everyone!

---

