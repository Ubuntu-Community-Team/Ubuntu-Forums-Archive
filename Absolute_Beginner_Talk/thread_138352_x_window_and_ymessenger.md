---
title: "x window and ymessenger"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by illusion on 2006-03-01
Hey,

I was trying to run the linux version of ymessenger.  Couldnt get it installed using dpkg, dependency failure.  Anybody know where a stabe copy is.  Secondly how do you use x window in ubuntu?

any help would be appreciated,
thanks in advance,
Illusion

---

### Post by Pragmatist on 2006-03-05
> Couldnt get it installed using dpkg
Give us the link where you downloaded the package.

>  how do you use x window in ubuntu?
X is the Graphical User Environment (GUI) for Linux
If your system has windows and menus and such, you ARE using X

Unlike some other operating systems, Linux can be used with or without a GUI. The graphical programs that you run, are X applications and run on top of X.  X is just a program; a very powerful program.  It can even have several instances running simulaneously, just like other programs such as wordprocessors.  Like other programs, it can be stopped and then started again without rebooting your machine.  Programs that don't require X can be run in or out of the X environment.  

To know more go to: [www.tldp.org](www.tldp.org) and do a search for "X howto"  you can also type ```
man X
``` in a terminal and read the man page for X

---

### Post by Zeroangel on 2006-03-05
[QUOTE=illusion]Hey,

I was trying to run the linux version of ymessenger.  Couldnt get it installed using dpkg, dependency failure.  Anybody know where a stabe copy is.  Secondly how do you use x window in ubuntu?

any help would be appreciated,
thanks in advance,
Illusion[/QUOTE]
Dependency failure usually means that you need to install additional components to get that program to install. What kind of dependencies does it have? And if you know what they are see if you can download them using synaptic or apt-get.

X-Windows is the name of the graphical server that hosts desktop environments like KDE and GNOME. You 'use' X-Windows by clicking on the 'x' button or minimize, or basically interacting with the computer, menus, windows, etc using your mouse in any way.

GAIM supports MSN and Yahoo messenger accounts if you didn't already know that.

---

