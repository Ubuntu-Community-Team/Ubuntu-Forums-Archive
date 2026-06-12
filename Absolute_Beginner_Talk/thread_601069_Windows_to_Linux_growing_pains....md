---
title: "Windows to Linux growing pains..."
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by fonger on 2007-11-02
For some reason, when I was using Windows, I didn't think twice when I installed a program, but now that I'm starting to use Linux, I feel I **have** to know how an installation works. Because of that, I've been trying to avoid using apt-get whenever I can, with less than stellar results.

Can someone point me to a truly newbie guide as to how to manually install programs, libraries and such? 

Sorry if this has already been asked before, but I feel if I'm to truly appreciate the liberating feeling of Linux, I have to at least be able to compile from source and install it. Thanks folks. I feel like a kid again.

---

### Post by Dr Small on 2007-11-02
Apt-get would be your easiest route, considering that it downloads the neccessary packages (and dependencies) to your system and installs them for you.

If you are not using Apt-get then most likely you would have to compile things, or use deb's.
Just use synaptic, Add / Remove or Apt-get. They are your easiest bet ;)

---

### Post by tarchy on 2007-11-02
I THINK you mean this..

Extract the file to your desktop
Terminal --> cd /home/USERNAME/Desktop FILENAME.tar.gz --> ./configure --> make --> make install

---

### Post by fonger on 2007-11-02
And I certainly appreciate the apt-get and Synaptics... from the bottom of my heart, I truly do. But again, this is more a quest for enlightenment more than anything else. 

The one thing that pissed me off about Windows was basically how little control I had over anything, and now supposedly with a more transparent Linux, I'd like to at least be able to understand that.

---

### Post by rsambuca on 2007-11-02
If you open up the Synaptic Package Manager, you can select a package that you have already installed, and then right-click -> Properties.  Under the Installed Files tab, you will see every file and directory that was altered and where every file was put.  An after the fact kind of thing, but at least it shows you everything.  

Frankly, if you wan't to uber-control everything prior to installing, then Ubuntu is definitely not the distribution that you want to be using.

---

### Post by supersonicdarky on 2007-11-02
> **tarchy said:**
> I THINK you mean this..

Extract the file to your desktop
Terminal --> cd /home/USERNAME/Desktop FILENAME.tar.gz --> ./configure --> make --> make install
just to add to this, **checkinstall** (instead of **make install**) is better because it first creates a deb before installing, which then can be easily removed

---

