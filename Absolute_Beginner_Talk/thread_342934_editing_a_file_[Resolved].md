---
title: "editing a file [Resolved]"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by Hamm on 2007-01-20
I need to edit a ini files for a game server I am running. It tells me I don't have rights to do that. how do I do that?

Hamm

---

### Post by aysiu on 2007-01-20
With *sudo*

```
sudo nano -B /path/to/file
```

More info here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bodhi.zazen on 2007-01-20
sudo <editor> <file>

for vi, nano

or if you use gedit,

gksudo gedit <file>

---

### Post by freebeer on 2007-01-20
You can give yourself temporary "superuser" status (and thereby have read/write priveledges) with the sudo command.

```


sudo gedit /path/to/filename


```

You'll be prompted for **your** username's password.  Just type in the password and the editor will launch, loading your file.

---

### Post by Hamm on 2007-01-20
I got done what I needed. I as so had to change the attributes of the file too.

---

