---
title: "Gnome Vs. KDE"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by aseem_mal on 2006-02-05
Hi. For a total Ubuntu Noobie (i.e., me), can one of the veterans explain what Gnome and KDE are? Almost on a daily basis, I hear this application is for KDE, or GNome. Also, when you come to Ubuntu Forums, they have posts/threads for Gnome and KDE...:confused: 

Please someone enlighten in simple terms for a Windows user.

Thanks in advance,
A

---

### Post by Klaidas on 2006-02-05
GNOME and KDE are graphical desktop environments.

Here is a cool comparison of them: [http://opensourceversus.com/modules.php?op=modload&name=News&file=article&sid=447&mode=thread&order=0&thold=0](http://opensourceversus.com/modules.php?op=modload&name=News&file=article&sid=447&mode=thread&order=0&thold=0)

Website of KDE: [http://www.kde.org](http://www.kde.org)
Website of GNOME: [http://www.gnome.org](http://www.gnome.org)

Ubuntu comes with GNOME, Kubuntu comes with KDE

Choose which one you prefer, "which one of these is better" is a non-ending flamewar :D

---

### Post by deadgoon on 2006-02-05
Gnome and KDE are "desktop environments."  That means they control all aspects of your graphical user interface.  This includes window decorations, menus, screensavers, application associations, etc.  Basically, the both do what Windows does, except each in its own way.

I would recommend installing Ubuntu.  It defaults to the Gnome desktop.  Once installed, you can install KDE later.  Then you can use either Gnome or KDE and pick the one you like.

To illustrate the difference, lets say you have everything installed.  When you log in you choose Gnome.  While logged in you change the desktop background, delete some menu items, change the association for text files to openoffice, and set the screensaver to come up after 1 minute.  Each time you log into Gnome, you will be able to see these changes.  Now you log out and log back in under KDE.  You will notice that there is a different desktop picture, different menu items, text files are associated with a different program, and the screensaver has changed.  You can easily change these to make them act as the do in Gnome, and once changed they will be the same each time you log into KDE.

I recommend picking Gnome since it is the default with Ubuntu.  Once you are settled in and are familiar with it, you can log in under KDE and learn it as well.  I do recommend installing KDE, even if you never use it because it comes with a great set of applications.  These applications will run under Gnome just as easily as KDE.

---

### Post by bartbes on 2006-02-05
It's just taste, as Klaidas said (well, he said something meaning that). KDE is more like windows, but if you don't like KDE or GNOME anymore you can just switch... (Your old desktop will stay on your pc)

Ubuntu (GNOME) to KDE:```
sudo apt-get install kubuntu-desktop
```
Kubuntu (KDE) to GNOME:```
sudo apt-get install ubuntu-desktop
```

TIP: If you want to do the switch faster you can first use ```
sudo apt-cdrom
``` and put in the install cd (it then gets most packages of the cd)

---

### Post by aseem_mal on 2006-02-05
Thank you all. That sure was very very enlightening. :)

- A

---

### Post by gabhla on 2006-02-05
I'm also new to this.  Have been on Linux 100% for over six months now - I've learned alot and it's been a great experience, actually it's been fun.  However, the issue of Gnome vs. KDE is very hard for me.  I like them both.  I honestly don't know which I prefer.  Each has it's own pluses and minuses, but taken together none of these differences amount to much.  

As a newbie myself, I'd recommend Gnome initially.  Get used to it, tinnker with it ... then try KDE and see which one you prefer.  I like them both...KDE offers a tad more options, but it's not as user friendly as KDE.

---

### Post by bartbes on 2006-02-05
[QUOTE=gabhla]KDE offers a tad more options, but it's not as user friendly as KDE.[/QUOTE]
Think you mean GNOME at one of those. I started with GNOME as well, and at first I hated KDE but when I started KDE after a certain amount of time (about 2 weeks :p ) I suddenly loved it, maybe it's because I find GNOME too easy... but as I said it's just taste

---

### Post by Klaidas on 2006-02-05
[QUOTE=gabhla]I'm also new to this. I've learned alot and it's been a great experience, actually it's been fun.  However, the issue of Gnome vs. KDE is very hard for me.  I like them both.  I honestly don't know which I prefer.  Each has it's own pluses and minuses, but taken together none of these differences amount to much.[/QUOTE]

Hehe :) That's exactly how I felt when I started using Linux. I sometimes feel that way now, but so far I'm using GNOME :)

---

### Post by AndyCooll on 2006-02-05
Of course you don't have to settle with either Gnome or KDE, there are other window managers such as XFCE, IceWM, Enlightenment...

And just because you choose a particular desktop doesn't mean you have to settle for that desktops applications as well. You can run KDE apps on a Gnome desktop environment and vice-versa.

:cool:

---

### Post by az on 2006-02-05
I think it's helpful to know how things are stacked up on each other.  It not just one chunk of programs that are your desktop but a few layers.

Lets say you are running firefox.  Firefox is displayed on your screen by a window manager.  The windows design and placement is handled by the WM.  Usually the WM has a panel with icons and access to a menu where you can start applications by clicking.

The WM is part of a desktop environment.  The desktop environment is responsable for providing a framework for applications to plug into so that they can all look the same and talk to each other.  For example, Gnome uses cups for printing.  All Gnome applications will use printing the same way.  If you run just a window manager, you need to specify which cammand to run to print something for each individual application.  This is tedious.

The DE runs on a display manager.  The display manager is started by init when you boot.  It is the application that logs you or another user into a DE.  From any DM, you can chose from the available DEs.

The DM run on top of the X server.  It is the thing that gives you a graphical environment.  It is the interface between the applications and the video hardware.

So you have this all stacked up:

Mozilla FF
Window manager (Metacity)
Desktop environment (Gnome)
Display Manager (GDM)
X server (Xorg)
Kernel (linux)

---

### Post by annsachd on 2006-02-05
Gnome is like Apple's OS X and KDE is like Microsoft's Windows.

I've heard this one a bunch of times.

---

