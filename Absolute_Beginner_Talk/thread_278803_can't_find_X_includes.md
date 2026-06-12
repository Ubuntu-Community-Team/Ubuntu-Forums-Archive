---
title: "can't find X includes"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by sriniwins on 2006-10-16
I am trying to install ns2 simulator on ubuntu in gnome and I get the following error

can't find X includes
otcl-1.9 configuration failed! Exiting ...

I have installed libx11-dev, xutils,x-dev and libxext-dev packages but am still getting the error. 

any ideas about how to overcome this.

---

### Post by turo on 2006-10-17
TTT, I have the same problem and I am unsure as how to fix it.

---

### Post by ozwolverine on 2007-08-21
Hello guys,

I hope this answer isn't quite late for you, if it is, I know it won't be for other new people with this problem :). I have had the same issue installing NS2, now I have found what package we need to install before otcl, tclcl, and ns2, the package is:

tk8.4-dev

At least for my ubuntu edgy (6.10) I did install it and now I was able to install it :)

Hope This help anyone,

OzWolverine

---

