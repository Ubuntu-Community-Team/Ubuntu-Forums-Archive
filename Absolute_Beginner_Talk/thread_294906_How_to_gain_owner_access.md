---
title: "How to gain owner access?"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by Charkel on 2006-11-07
How can i log in as the owner. It says "You are not the owner so you can't change these rights" <- Translated from swedish. Might say admin instead of owner.

I'm on the one and only admin account tho.


Also i have a second question. How to delete the writing protection* of a file (menu.lst in this case)


*Named like that in english?

---

### Post by bluenova on 2006-11-07
In what?

If you are trying to browse files do: CTRL + ALT + F2 and type:

gksudo nautilus

After typing your password, you can then browse with full rights.

---

### Post by jimbren on 2006-11-07
You can grant yourself admin, or Root, access by using the sudo command and your password.  

So if you want to edit the menu.lst file, you would do something like this from /boot/grub:

```
sudo nano menu.lst
```

You can change the permissions on a file by using the chown command, but you want to be very careful with that.  Some things can break just with a permissions change, and you can also accidently do major harm to your system if you take ownership and make an inadvertent mistake. 

Does that make sense?

---

### Post by jimbren on 2006-11-07
Also, if you wanted to use a graphical editor like gedit or kwrite to edit a file, then you would want to use a slight different command.

If you're in Gnome, you would use gksudo, and in KDE you would use kdesu

So it would look like this:
gnome:
```
gksudo gedit /etc/somefile
```

kde:
```
kdesu kwrite /etc/somefile
```

---

### Post by CatKiller on 2006-11-07
These two pages will tell you what's going on:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

