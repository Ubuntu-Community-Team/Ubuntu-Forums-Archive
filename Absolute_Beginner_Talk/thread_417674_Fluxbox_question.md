---
title: "Fluxbox question"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by 3rr0r on 2007-04-21
Is fluxbox xubuntu?  I downloaded xubuntu and am actually posting from the cd right now :) 

I like the look and feel of the fluxbox desktop managers that I have seen, and am wondering if xubuntu uses this?  I read it uses xfce, but not sure if that is the same thing.  If not, is it possible to install fluxbox onto xubuntu, or would it be easier to d/l ubuntu and install fluxbox?  

Also, does xubuntu use gnome/kde environment or is the xfce its own (and equivalent) ?  I am worried about what programs I will be able to run and themes I will be limited to .  Thank you .

Sorry for all the questions.

---

### Post by Swab on 2007-04-21
XFCE and fluxbox are separate.   You can certainly install fluxbox along side XFCE, it's as simple as...
sudo apt-get install fluxbox
Then when you are logging in you can change session to use fluxbox!

---

### Post by Pobega on 2007-04-21
Xubuntu uses Xfce as a desktop environment and Xfwm as a window manager.
Fluxbuntu uses Fluxbox as a window manager (No default desktop environment enabled).

They are two competely seperate projects, and you can apt-get both of them from the Ubuntu repositories.

---

### Post by pjones0404 on 2007-04-21
xubuntu uses xfce. xfce is its own environment. fluxbox is another lightweight environment but it is different. in regards to what all is different i am not sure. 

when u install ubuntu you can add as many enviroments (kde/gnome/xfce/fluxbox) as u want. just keep in mind that u will need the storage pace for all of these. when u log in u can select which one u want to use for that session. u can also set one as a default to use.

---

### Post by 3rr0r on 2007-04-22
Ok, so in regards to Xubuntu.  I noticed that Ubuntu is GNOME while Kubuntu is KDE, and although they have programs that run in each native environment (Rhythmbox vs Amarok) each program can run in the other environment.

What does xubuntu use?  Will I still be able to use Gnome/KDE programs as well?  I'm just trying to figure out what I'll have access to or what will "cost" me more (in resources).  Thanks again.

---

### Post by yabbadabbadont on 2007-04-22
XFCE uses GTK like Gnome does.  You can run any linux program under any desktop environment as long as the program's dependencies have been installed.  And they will be as long as you use apt-get, aptitude, synaptic, adept, ...  (any one of the package managers available on the various flavors of ubuntu), to install your programs.

---

