---
title: "Updating GAIM to Pidgin"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by alecwh on 2007-06-14
Hey, just a quick question.

Ubuntu came with "Gaim", but as you know, Pidgin has been released since. I just install Pidgin as a .dub, but now I can't remove the old GAIM from my computer.

Can it be done?

---

### Post by Inxsible on 2007-06-14
you can do a 
```
sudo aptitude remove gaim
```

---

### Post by alecwh on 2007-06-14
I did exactly what you said, and my system crashed.

It said that it was removing "Ubuntu Desktop" or semething during uninstallation...

I'm on the live CD, reinstalling my OS. :(

---

### Post by Pink Splat on 2007-06-14
I just updated from gaim to Pidgin as well, I did what you said to remove gaim and it did successfully. While it was uninstalling gaim it did say something about uninstalling Ubuntu-desktop, kinda freaked me out but gaim is gone \\:D/ 

Before I read this I tried uninstalling it threw the Add/Remove programs and it wouldn't allow me to remove gaim saying that other programs depended on gaim in order to run properly, so far this is not the case.

---

### Post by alecwh on 2007-06-14
I just rebooted after, and it said there was a problem with X server.

Anyway, Installation complete. Rebooting.

---

### Post by Old Pink on 2007-06-14
I personally was threatened with> Remove the following packages:
nautilus-sendto

Leave the following dependencies unresolved:
gaim-data recommends gaim
xubuntu-desktop recommends gaim
Score is -701And just left GAIM on my system. It'll go with Gutsy Gibbon. :) 

I could modify the dependencies, but it can get messy. :P

---

### Post by Old Pink on 2007-06-14
Update: [http://www.mbhoy.com/14-06-2007/pidgin-201](http://www.mbhoy.com/14-06-2007/pidgin-201)

On the bottom of that post on my blog, I've uploaded a transitional package, that will remove GAIM.

For use after the installation of Pidgin. :)

---

### Post by xthund3rh3adx on 2007-06-14
just try this one:

sudo apt-get remove gaim

---

### Post by Inxsible on 2007-06-14
removing ubuntu-desktop should not be a problem. Its a meta-package which points to what packages should be installed.

You will have problems when you *upgrade* your OS. for eg Feisty to Gutsy.

But if you do a fresh install..it shouldn't be a problem. I still use Gaim, but i removed ubuntu-desktop when i removed  Evolution, and other pre-installed software that i didnt need.

---

### Post by ts51 on 2007-06-17
What is the SAFE way to remove Gaim? Now I am terrified to upgrade... 

Spent SO much time just to get to Linux...

---

