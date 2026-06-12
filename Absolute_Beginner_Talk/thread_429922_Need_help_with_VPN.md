---
title: "Need help with VPN"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Krystoll Meth on 2007-05-01
Trying to connect to my Ubuntu 7.04 home system from my windows XP office system.  I'm behind a router at home but we're able to connect to our office computers from home and vice versa, so I want to connect to my home system from there.  Need some help please

---

### Post by gerscht on 2007-05-02
You will need to have ssh running on your home machine
```
sudo apt-get install ssh
```
a great tool to connect from a windows machine using ssh is PuTTY [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)
This will give you only the command line though.
To get remote desktop access, look for VNC or a X11 through ssh tunnel in the forum.

Gerscht

---

