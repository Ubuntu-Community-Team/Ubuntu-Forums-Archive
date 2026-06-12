---
title: "sudo and gksudo"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-08-08
why should we use gksudo for GUI apps?

why not plain sudo?

---

### Post by igknighted on 2007-08-08
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

Aysiu does a great job of explaining it here.

---

### Post by rickyjones on 2007-08-08
I'm no expert but I believe that gksudo is supposed to be the graphical counter-part to the command-line sudo.

I believe that either can be used but when in a GUI it is recommended to use other GUI tools to accomplish the task.

Like I said, I'm no expert but I hope this is pointing in the right direction.

-Richard

---

### Post by skymera on 2007-08-08
thanks :)

the only thigs i run with sudo grapihcally

is gedit..

programs i use gksudo.
people reccomend so i use it

anyway thanks ofr help

---

### Post by overdrank on 2007-08-08
> **skymera said:**
> why should we use gksudo for GUI apps?

why not plain sudo?

Hi maybe this will help
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
Edit: to slow

---

### Post by skymera on 2007-08-08
got beaten to it :P

---

### Post by asmoore82 on 2007-08-08
sudo makes a GUI app connect to your X11 manager as root.
Users are not allowed to open GUI apps on other users X11 sessions;
so in other words, root is forcing his way into your X11 session.
gksudo is much more proper and safer because it runs a GUI app with root permission but
the Window is still a part of your userspace X11 session.

it is a subtle difference, much like the difference between 'sudo -s' and 'sudo -i'

---

