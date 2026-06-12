---
title: "Lost Ubuntu style startup"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Gaunty on 2007-05-04
I installed Ubuntu a few weeks ago and as I've been learning I fancied trying the kubuntu and Xbuntu desktops to see if I preferred them.  They have overwritten the default startup screens and I get the Xbuntu logon screen in blue and the Kubuntu shutdown screen.

Is there a simple way to get the Ubuntu screens back?

---

### Post by jargoman on 2007-05-04
if you are going to add a desktop manager like kde there are two ways of doing it from the command line

$ sudo apt-get kde

or 

$ sudo apt-get kde-desktop

the latter will change your system to a default kde settion

you most likely can get it back by gooing to System > Administration > login window and change it back to the default. In fact you can go to 
[www.gnome-look.org](www.gnome-look.org)
and get many custom login screens. Everything you can imagine can be changed in linux thats what makes it so cool.

---

### Post by Gaunty on 2007-05-04
Thanks for that, I found what I wanted by looking around that site for instructions on how to install a GDM theme.

The answer is:
sudo gdmsetup

:)

---

