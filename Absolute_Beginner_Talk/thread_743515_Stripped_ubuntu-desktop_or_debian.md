---
title: "Stripped ubuntu-desktop or debian?"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by saj0577 on 2008-04-02
Hey, anyone know where i can get a real stripped down version of ubuntu-desktop basically i only want the apps from the System part of the menu and all the ones that help run the computer non of the photo editing ones, office, multimedia etc.

Or is my best option getting a debian cd ?

Saj

---

### Post by meborc on 2008-04-02
if you download the alternative install cd, you are able to install only the command line system... this is as stripped as you can get it... you will have to install all the packages you want afterwards through the command line

the other way would go to debian home page and download the net-install cd

---

### Post by Rocket2DMn on 2008-04-02
I think the package you want is called "gnome-core" - [http://packages.ubuntu.com/gutsy/gnome-core](http://packages.ubuntu.com/gutsy/gnome-core)

---

### Post by saj0577 on 2008-04-02
I still want gnome and a few of its programs just not its games,gimp,firefox etc. I want more then a command prompt.

Saj

---

### Post by Medieval_Creations on 2008-04-02
The CLI, is just a starting point.
That's how I setup all my systems.  Do a CLI install and then run a script to install only the appz I want.

---

### Post by saj0577 on 2008-04-02
> **Rocket2DMn said:**
> I think the package you want is called "gnome-core" - [http://packages.ubuntu.com/gutsy/gnome-core](http://packages.ubuntu.com/gutsy/gnome-core)


Thanks, but what about the x server as well? Because just installing them (on a server for instance) would not give me an x server. I want a stripped down version that does not have all the programs under applications on the menu.

Saj

---

### Post by saj0577 on 2008-04-02
> **Medieval_Creations said:**
> That's how I setup my systems.  Just do a command line install, update a few config files and run a script to install the programs that I use.

You know what i need to install to install a x-server with gnome?Very basic.

Saj

---

### Post by Medieval_Creations on 2008-04-02
> **saj0577 said:**
> You know what i need to install to install a x-server with gnome?Very basic.
Saj

```
sudo apt-get install x-window-system
```

You could also try the gnome-core package.  I've never used it, but I would think that it would also install X.
You could also use xorg as a replacement for x-window-system.

Depending on you system you may have to install your video driver (ATI / nVidia)

---

### Post by Medieval_Creations on 2008-04-02
AFTER THOUGH:
 You would have to install a Window Manager as well... I use fluxbox personally so you would want to add which every you want to the install command as well (KDE, Gnome Fluxbox, etc.).

---

### Post by Rocket2DMn on 2008-04-02
The package for X I think is just xserver-xorg-core - [http://packages.ubuntu.com/gutsy/x11/xserver-xorg-core](http://packages.ubuntu.com/gutsy/x11/xserver-xorg-core)
gnome-core may be dependent on it, so it may install automatically when you try to install the gnome stuff.
The gnome-core should just be the basic gdm stuff without all the openoffice and other stuff.  This is what you want, isn't it?

---

### Post by Medieval_Creations on 2008-04-02
Here's the script the packages that I use to just get a GUI up and running after a CLI install.

```

# Core
sudo apt-get install x-window-system fluxbox slim restricted-manager xscreensaver xscreensaver-data-extra
xscreensaver-gl-extra alsamixergui eterm synaptic bum gtk-theme-switch gtk-chtheme pcmanfm leafpad unzip

```

---

### Post by saj0577 on 2008-04-02
Thanks everyone. All very helpful. Yeah i been looking and i though i might have to install each package so. gnome-panel gnome-panel-data etc and was trying to find a list like this.

I was just a little confused when i found the package gnome and it was not installed on my current system. :S

Saj

---

### Post by Rocket2DMn on 2008-04-02
If you installed the server edition of Ubuntu, a GUI is not installed by default.  If you did the Desktop version, it is possible you elected somewhere along the way to NOT install the GUI stuff, this has been known to happen before.

---

### Post by saj0577 on 2008-04-02
Its a server install which im trying to get a very basic GUI on, without using ubuntu-desktop otherwise i would just use the ubuntu-desktop install cd.

Saj

---

### Post by click4851 on 2008-04-02
Just a thought, you could try Xubuntu....pretty light weight, full featured, remove any extras ya don't want....?

---

### Post by EnergySamus on 2008-04-02
> **click4851 said:**
> Just a thought, you could try Xubuntu....pretty light weight, full featured, remove any extras ya don't want....?

That is a good idea:lolflag::)

EnergySamus

---

### Post by Rocket2DMn on 2008-04-02
Fluxbox is even more lightweight, it is what Medieval_Creations showed in post 11.  I've never used it, but I've heard good things about it.

---

### Post by rsambuca on 2008-04-02
Just do what is called a minimal installation.  It installs the basic requirements for a working system, and then you customize and add the packages you require.  The instructions are here on this page.  It says for [LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems"), but it obviously works for any system.  It also gives ideas as to what packages you will require for a minimal desktop environment.

---

### Post by Rocket2DMn on 2008-04-02
Good call rsambuca, you can get more info about a similar Minimal Install here - [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by saj0577 on 2008-04-03
Cheers guys.

About the xubuntu sugestion. I like xubuntu i have it on my sessions list but i just prefer gnome :)

Saj

---

