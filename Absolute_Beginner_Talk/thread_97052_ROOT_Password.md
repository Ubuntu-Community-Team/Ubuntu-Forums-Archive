---
title: "ROOT Password"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by RhinoHornZa on 2005-11-30
Hi guys.. Need Help.

  Recently installed Unbuntu 5.10 ( (very new to me), did not get the option for root password when I did the installation.  I now need to run pppconfig to set up my dial up internet connetion, but I require a root password, which I don't have.

Any help?

---

### Post by linbetwin on 2005-11-30
Enter your user password. That'll give you root privileges.

---

### Post by teaker1s on 2005-11-30
you use 'sudo' command or 'gksudo' for gui to access root and the password is the same as your login

---

### Post by linbetwin on 2005-11-30
Also, read this:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by patrick295767 on 2005-11-30
try to type :
```
sudo su
```
and password installation user if u didnt change it yet
   
If you really cant get it and know another psswd, u can have also a look there:
[http://www.ubuntuforums.org/showthread.php?t=64557&page=6](http://www.ubuntuforums.org/showthread.php?t=64557&page=6)
 Good courage !

---

### Post by Lofticus on 2005-11-30
I have a question on that GUI sudo thingy, if I run nautilus, how can I explain to it to gain su rights?

---

### Post by Kvark on 2005-11-30
[QUOTE=Lofticus]I have a question on that GUI sudo thingy, if I run nautilus, how can I explain to it to gain su rights?[/QUOTE]
Type "gksudo nautilus" in a command line, or make a launcher on the panel or desktop with that as the command.

---

### Post by ex` on 2005-11-30
[QUOTE=Kvark]Type "gksudo nautilus" in a command line, or make a launcher on the panel or desktop with that as the command.[/QUOTE]
Or install the 'root-nautilus-here' script, which you can find [here](http://g-scripts.sourceforge.net/nautilus-scripts/Execute/Misc/root-nautilus-here).
nautilus scripts folder is .gnome2/nautilus-scripts under your home dir.

(This will add a "Scripts -> root-nautilus-here" section to your rightmouse menu's)

This is also available in automagix, which might be worth looking at, as well. :)

---

### Post by basketcase on 2005-11-30
[QUOTE=ex`]Or install the 'root-nautilus-here' script, which you can find [here](http://g-scripts.sourceforge.net/nautilus-scripts/Execute/Misc/root-nautilus-here).
nautilus scripts folder is .gnome2/nautilus-scripts under your home dir.

(This will add a "Scripts -> root-nautilus-here" section to your rightmouse menu's)

This is also available in automagix, which might be worth looking at, as well. :)[/QUOTE]
This is a great tool....great for when you want/need to edit a file and need root access

---

