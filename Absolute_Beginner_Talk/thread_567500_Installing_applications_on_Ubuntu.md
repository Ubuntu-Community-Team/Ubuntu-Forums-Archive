---
title: "Installing applications on Ubuntu"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by zxzlenin on 2007-10-04
Hi all,im new to linux just installed like 2 hours ago my only problem is i cant installed any applications i download like,java,flashplayer "Cant open.bin".I read some stuff about using
Applications>Accesories>Terminal but i have no idea how to make that work.And another thing i tried to move a folder from destktop to the Amsn plugin directory and it says i dont have persmission to write their >< im only user i saw : System>Administrations >Users And groups and checked all the priviledges.


Thx !

---

### Post by Billy_McBong on 2007-10-04
[COLOR="Blue"]System>Administration>Synaptic Package Manager
you can install many programs through that[/COLOR]

---

### Post by bodhi.zazen on 2007-10-04
[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)

It is a stick in Absolute Beginner Talk : "Complete Guide to Installation in Ubuntu"

---

### Post by zxzlenin on 2007-10-04
kk thx for the guide

---

### Post by SpiritIsReality on 2007-10-04
howdy
link here talks about rootsudo (the one with all the permissions, you)
[https://help.ubuntu.com/community/RootSudo?highlight=%28gksudo%29](https://help.ubuntu.com/community/RootSudo?highlight=%28gksudo%29)
if hold down Alt key, and press F2 key, then let all up, get a run box.
if in run box, type 
```
gksu nautilus
``` 
you have a file browser open as root, no permission troubles, but we all know what that means. haha!
buds
edit: oops. If I'd known there was all this traffic I'd have just listened.

---

### Post by Ub1476 on 2007-10-04
Installing software is really easy in Ubuntu. Just click on Applications>Add/Remove (also known as Synaptic) then search for what you need. If you want to download and install Java, search for "java" and install the plugin. There's a box below which contains description for what it is and does. However, since java (and many other applications) is not open-source, you have to choose "All available applications" in the upper-right corner. 

If you don't plan on using beta software, you probably don't need to use the Terminal, unless you want to.

Hope that helps:popcorn:

Edit: If you plan on messing around in the File system (which it looks like you want to do when adding themes to amsn), you most open the terminal and type:

```
sudo cp /where/your/theme/is/.theme /to/destination/folder
```

---

