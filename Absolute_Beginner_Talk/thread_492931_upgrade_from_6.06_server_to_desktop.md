---
title: "upgrade from 6.06 server to desktop"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by JsATL on 2007-07-05
I installed 6.06 LTS server and I see there is no desktop, it's all command line. 
I would like to upgrade :

A) to a graphical desktop but keep the server functionality

B) get all the latest and greatest packages (ie 7.04)

PROBLEMS: There is no 6.10 image available for download and the documentation says I cannot go directly from 6.06 to 7.04 --too risky.

I tried gksu "update-manager -c"  but says WARNING: cannot open display

QUESTION: does 6.06 LTS server have a graphical mode BUT my card is not recognized?
I'm running NVIDIA RIVA TNT2. 

In Red Hat I've used Xconfigurator, etc.

Can I get into graphical desktop mode using 6.06 LTS??  Maybe then I can upgrade using gksu.....

---

### Post by coolen on 2007-07-05
> **JsATL said:**
> I installed 6.06 LTS server and I see there is no desktop, it's all command line. 
I would like to upgrade :

A) to a graphical desktop but keep the server functionality

B) get all the latest and greatest packages (ie 7.04)

PROBLEMS: There is no 6.10 image available for download and the documentation says I cannot go directly from 6.06 to 7.04 --too risky.

I tried gksu "update-manager -c"  but says WARNING: cannot open display

QUESTION: does 6.06 LTS server have a graphical mode BUT my card is not recognized?
I'm running NVIDIA RIVA TNT2. 

In Red Hat I've used Xconfigurator, etc.

Can I get into graphical desktop mode using 6.06 LTS??  Maybe then I can upgrade using gksu.....

Try to install the ubuntu-desktop package (or whichever desktop you want to use).
From there, try upgrading...I don't know if you can upgrade to Edgy, or if it'll try to put you into Feisty. I've never upgraded directly...I always had the good fortune to need to reinstall by the time the next release came out :)

---

### Post by LuckyDevil on 2007-07-05
sudo apt-get update - to update your sources
sudo apt-get dist-upgrade - to upgrade to the latest distribution (i.e. 7.04)
sudo apt-get install ubuntu-desktop - install gnome desktop environment with all the goodies
sudo apt-get install gdm - install the gnome desktop manager

Hope that helps!

EDIT - Sorry, I just noticed you didn't want to jump from 6.06 directly to 7.04...my apologies for replying before reading fully :-(
I believe you could grab an image of the 6.10 install disk on some torrent sites still (i'm at work, so i can't verify that for you), you should just be able to pop the disk in and it will prompt the upgrade.

---

### Post by Seisen on 2007-07-05
Your best bet in all honesty if you tring to keep it as a server would to install Fluxbox, Openbox, etc. something very lightweight.

The unofficial way of upgrading to the new distro is to change Dapper to Edgy in your source list. This link is for low memory systems but you can use it to keep you gui at a minimum.

[https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

---

### Post by coolen on 2007-07-05
> **LuckyDevil said:**
> sudo apt-get update - to update your sources
sudo apt-get dist-upgrade - to upgrade to the latest distribution (i.e. 7.04)
sudo apt-get install ubuntu-desktop - install gnome desktop environment with all the goodies
sudo apt-get install gdm - install the gnome desktop manager

Hope that helps!

ubuntu-desktop depends on gdm anyway :)

---

### Post by az on 2007-07-05
> **coolen said:**
> ubuntu-desktop depends on gdm anyway :)

To run a desktop on any hardware, you should also install the generic kernel since the server kernel will not work with all desktop hardware (like some mice, for example)

sudo apt-get install linux-generic ubuntu-desktop

Once you have installed that, get into the desktop

sudo init 2

and then use the update-manager command to dist-upgrade to Feisty.

It would be faster to just download the feisty desktop cd, install that over top of your current install and then install LAMP on top of that:

Open a terminal and run

sudo tasksel

and pick LAMP.

There is no desktop version or server version.  They are just packages.  You can install the LAMP stack on a desktop and it will work just fine.  You should not do this on a production server, though.
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

