---
title: "Can't display as SU"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by age99 on 2008-03-04
I'm trying to display various applications on the terminal when I'm the SU.  Basic stuff like nedit or gedit, but I get this error:

Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
NEdit: Can't open display

I'm guessing that I will have to change something in the .bashrc?

Can anyone give me a hand?  Thanks!

---

### Post by bodhi.zazen on 2008-03-04
Try gksu (as a user, not root)

gksu <Application>

Ex: gksu gedit

Note: Use kdesu with Kde

---

### Post by age99 on 2008-03-05
Loading the applications are fine as a user, but I just can't display anything as root.  If I am root (after "su -" command) I tried to do the "gksu gedit" but there were still the same errors.

---

### Post by bodhi.zazen on 2008-03-05
Well, you are obviously having problems with X, I presume Xauthority, hard to know exactly.

As I indicated the "proper" way to run X apps as root is with gksu, which is run as a user and not root.

Please run the application as a user via gksu rather then su to root.

If gksu fails , post the error message.

gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

