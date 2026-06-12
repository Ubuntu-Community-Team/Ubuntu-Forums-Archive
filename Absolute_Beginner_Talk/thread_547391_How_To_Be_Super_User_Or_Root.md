---
title: "How To Be Super User Or Root"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by mrsurf on 2007-09-10
Plz Let Me Know How To Be Root In Ubuntu 7.04

---

### Post by aysiu on 2007-09-10
You don't need to be root. Read this:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

---

### Post by Dylock on 2007-09-10
usually if you are just executing single commands, you use sudo

```

sudo MYCOMMAND

```

If you need to be the superuser (not recommended)
look into the su command

you can foobar your system by being in root though

---

### Post by steveneddy on 2007-09-10
> **Dylock said:**
> usually if you are just executing single commands, you use sudo

```

sudo MYCOMMAND

```

If you need to be the superuser (not recommended)
look into the su command

you can foobar your system by being in root though

dang - you beat me to it...

---

### Post by steveneddy on 2007-09-10
> **aysiu said:**
> You don't need to be root. Read this:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

hey aysiu - good to see you some more around the forums.

take care.

---

### Post by aysiu on 2007-09-10
> **Dylock said:**
> 
If you need to be the superuser (not recommended)
look into the su command

you can foobar your system by being in root though You can also "foobar" your system with *sudo*. I wouldn't recommend enabling a root account for most home users mainly because it's unnecessary and (counterintuitive though it may seem at first to the new user) inconvenient. *sudo* is designed to be secure and convenient, which is why both Ubuntu and Mac OS X use it.

---

### Post by mrsurf on 2007-09-11
Will sudo work out for even changing file permissions. That is i want to create a new file in the root (grub) system it says no permissions
Thanks in advance

---

### Post by bodhi.zazen on 2007-09-11
Yes, but you should be saving most things in /home/<user_name>

---

### Post by Uren2 on 2007-09-15
I'm trying to install software and it won't let me drag and drop into /usr/local/<destination directory>.  Another forum member suggested giving my user account full admin privileges.  Can anyone shed some light on how to do that?  I've made sure that all the permissions for this account are checked in User Management.

Please disregard, some helpful forum members have already shown me what to do in another thread.

---

### Post by Tyke91 on 2007-09-15
exactly what kind of software are you installing?


and you can give yourself a temporary root nautilus explorer with gksudo, but that is unadvised for the same reason that having a root account is unadvised...

---

### Post by Dylock on 2007-09-15
> **Uren2 said:**
> I'm trying to install software and it won't let me drag and drop into /usr/local/<destination directory>.  Another forum member suggested giving my user account full admin privileges.  Can anyone shed some light on how to do that?  I've made sure that all the permissions for this account are checked in User Management.

just curious, is it something that you could use synaptic to install?

If your going to be doing anything that needs SU privs, you should be using sudo

like sudo cp /home/foo/bar/myfile /usr/local/somewhere

---

### Post by Kilz on 2007-09-15
You could also open a terminal and type in ```
gksudo nautilus
``` This will open up nautilus as an adminstator. You can then drag and drop files all over the file system, change permissions, and delete them. But be careful it is possible to fubar your system.

---

### Post by Uren2 on 2007-09-15
I was installing mozilla seamonkey.

---

### Post by Uren2 on 2007-09-15
I looked for it in synaptic, but I couldn't find it.

---

### Post by Kilz on 2007-09-15
> **Uren2 said:**
> I looked for it in synaptic, but I couldn't find it.

[Go here,]("http://www.mozilla.org/projects/seamonkey/") download the linux installer. Right click on the tarball and choose extract here.
Open a terminal and navigate to the folder it extracts, if the folder is on the desktop the command is.
```
cd ~/Desktop/seamonkey-installer
```
run the installer with 
```
sudo ./seamonkey-installer-bin
```

---

### Post by Uren2 on 2007-09-19
Thanks Kilz :D  and everyone who posted advice!

---

