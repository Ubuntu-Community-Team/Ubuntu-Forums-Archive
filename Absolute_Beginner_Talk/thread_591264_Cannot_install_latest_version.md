---
title: "Cannot install latest version"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by vnmispoisn on 2007-10-25
[http://www.metatube.com/image-hosting/uploads/45e476fdeb.png](http://www.metatube.com/image-hosting/uploads/45e476fdeb.png)

Here is a screenshot of the error message I get. How do I install the latest version of ubuntu?
I am new to linux so please let me know in layman's terms.

---

### Post by misfitpierce on 2007-10-25
terminal

sudo dpkg --configure -a

Says in that window.

Whenever a window says must do something manually with a command you usually whip terminal out and put command it shows in it, most times with sudo in front of it which gives you admin/superuser privileges.

---

### Post by Maestro23 on 2007-10-25
Open a terminal and run the command** it tells you to.**

> sudo dpkg --configure -a

Then try your updates again.

---

### Post by vnmispoisn on 2007-10-25
got it. thanks for the help

---

