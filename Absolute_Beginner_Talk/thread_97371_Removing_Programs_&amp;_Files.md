---
title: "Removing Programs &amp; Files"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2005-11-30
I am trying to remove Mathematica manually because there is no uninstaller and **sudo apt-get remove mathematica** does not work.  I am trying to delete /usr/local/Wolfram, but it won't allow me to, even after changing ownership to my username 'alex' and chmod 700.  Any ideas why this is?

---

### Post by Xian on 2005-11-30
There is a command you can use but it is too easy to goof up and actually start deleting a lot of things that your system needs. It is better to start up Nautilus as admin, navigate to the directory and remove it with a right-click send to trash.

$ sudo nautilus

[QUOTE=apmcavoy]Any ideas why this is?[/QUOTE]
Because the parent folder does not give you write access.

---

