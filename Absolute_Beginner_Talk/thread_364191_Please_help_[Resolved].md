---
title: "Please help [Resolved]"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by dudeness3 on 2007-02-17
I know I ask a lot of questions, but I'm starting to get frustrated, I would like to install some brushes in GIMP, but I can't because my computer is telling me I am not root, when I know for a fact that I am, it feels like I have 0 permissions. I can't do anything, because my computer says I don't have permissions, please someone tell me how to install brushes in my GIMP before I go crazy! Or tell me how to get all the permissions I should have.

---

### Post by nonewmsgs on 2007-02-17
sudo gives root priviledges so something like sudo pico 
im noob new so i dont know what brushes are

---

### Post by dudeness3 on 2007-02-17
I know that, but I need GIMP help, or to know how to log in to root, because you can't on the login screen.

---

### Post by Maestro23 on 2007-02-17
> **dudeness3 said:**
> I know I ask a lot of questions, but I'm starting to get frustrated, I would like to install some brushes in GIMP, but I can't because my computer is telling me I am not root, when I know for a fact that I am, it feels like I have 0 permissions. I can't do anything, because my computer says I don't have permissions, please someone tell me how to install brushes in my GIMP before I go crazy! Or tell me how to get all the permissions I should have.

What type of file is it? What directory did you d/l it to?

---

### Post by aysiu on 2007-02-17
Alt-F2 ```
gksudo nautilus
``` Or if the brushes get installed through GIMP itself ```
gksudo gimp
``` More info here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by adza on 2007-02-17
start gimp from the terminal with sudo gimp... that should let you run it as root... as for starting from the panel or menus with root access? If someone else knows how to do this that would be handy.. solve some of my ET issues! hehehe... however this will let you run gimp as root....

---

### Post by aysiu on 2007-02-17
> **adza said:**
> start gimp from the terminal with sudo gimp... that should let you run it as root... as for starting from the panel or menus with root access? If someone else knows how to do this that would be handy.. solve some of my ET issues! hehehe... however this will let you run gimp as root....
```
gksudo gimp
``` is the appropriate command, since GIMP is a graphical (not a terminal) application. *sudo* is for terminal applications.

More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by dudeness3 on 2007-02-17
Thank you so much, I almost lost it.
You sir, win an entire internet!
I just went through Nautilus

---

### Post by Maestro23 on 2007-02-17
Brushes are stored in:

/home/username/.gimp-2.2/brushes

---

