---
title: "how to turn Ubuntu again in gnome desktop"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by desiretosee on 2007-03-13
Hi! 
I installed Ubuntu 6.10 Edgy yesterday. I need Kile as well. The Kile need KDE components. As I have already had nightmare with Fedora 6 because of collision between KDE and Gnome. So I switched Ubuntu into Kubuntu. But still I can not install Kile. 
funny is, under Gnome there is still an option you can choose, if you want to install Kile or Lyx . but under Kubuntu, there is no such items.

So first of all I want to switch to Gnome. How can I do that?:confused: 
Second, how can I install Kile under Gnome Desktop?:confused: 

Thanks a lot for your help?

best regards

---

### Post by rich.bradshaw on 2007-03-13
Why won't it install? How are you installing?

Surely a 

sudo aptitude install kile

should do the trick, I don't think that it will mess things up having some KDE libraries installed - I have done this before and had no problem.

When you say that it won't install, what do you mean? Do you get an error of some sort?

---

### Post by rich.bradshaw on 2007-03-13
sudo apt-get remove kubuntu-desktop
sudo apt-get install ubuntu-desktop

I think will get you back to gnome.

Let someone else verify that first, I haven't done it myself.

If Gnome is still installed, just choose it when you log in. If you autologin, press ctrl-alt-backspace, then at the login screen choose GDM or gnome from the sessions menu. (Or something like that, not at a Linux machine currently.)

---

### Post by desiretosee on 2007-03-13
Thank you very much! I will try. I have not so much knowledge about command. I can only follow the graphic orders. is the last tip you gave to me command? so I should first run terminal?

---

