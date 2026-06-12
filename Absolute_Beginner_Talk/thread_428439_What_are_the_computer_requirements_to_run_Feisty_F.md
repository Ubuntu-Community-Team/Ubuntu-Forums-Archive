---
title: "What are the computer requirements to run Feisty Fawn?"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by purplearcanist on 2007-04-30
What are the computer specs required to run Feisty Fawn.
Sorry that this is a newbie question, as I tried to search for the information.

I have a 663 Mhz processor, about 128 MB of ram, and about 13 GB of hard drive space.
Will I be able to run the new version with this much?

---

### Post by LaRoza on 2007-04-30
You could run it, but you might want a less graphics intense Distro, Xubuntu would be good for Ubuntu. You could get more RAM, which would enable it to run faster.

---

### Post by dptxp on 2007-04-30
RAM too low. 256 MB minimum needed.
Maybe you can install and run with alternate CD. 
Xubuntu may be your option. But no Live CD in Xubuntu too.
Alternate CD to install.

---

### Post by purplearcanist on 2007-04-30
But is it easy to install Xubuntu from Ubuntu, too ? (Preferably without a CD)

Also, I was just guessing at the ram.  I don't know if it is 128 or 256 MB.

I might need to upgrade the computer.

---

### Post by on.journey on 2007-04-30
Feisty runs on my Pentium II 566 and 12 GB, plus memory ram of 64 perfectly fine, so it should work for you without any problems. However, if you're planning to customize your interfface Is uggest it's not the best solution.

---

### Post by Outrunner on 2007-04-30
You'll want to download an Xubuntu 7.04 Alternate CD from [HERE]("http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/") and install trough text mode(or you might want to install the command-line version and download a lightweight Window Manager like IceWM)

---

### Post by Sef on 2007-04-30
> But is it easy to install Xubuntu from Ubuntu, too ?

You could do a server install, then type these commands to get [Xubuntu]("http://xubuntu.org").

```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

The above commands were taken from [Psychocat's installing Xfce]("http://www.psychocats.net/ubuntu/xubuntu").

---

### Post by purplearcanist on 2007-04-30
Also, I forgot to mention that I already have Ubuntu 6.10 Edgy Eft installed.

I'm probably going to change to 6.10 Xubuntu.

---

### Post by DJiNN on 2007-04-30
> **purplearcanist said:**
> Also, I forgot to mention that I already have Ubuntu 6.10 Edgy Eft installed.

I'm probably going to change to 6.10 Xubuntu.

Why don't you just do a dist-upgrade & find out? If you're already running Edgy, then it's probably going to be easier to do that than install from scratch, and it should work fine. 

128mb Ram is fine (if a bit on the low side) and should cope OK. Xubuntu would be a better bet than the Gnome Ubuntu desktop.

If you'd like to install a really good lightweight distr, that's based on Feisty, then wait a few weeks for the Feisty release of [Fluxbuntu]("http://www.fluxbuntu.org") which is the equivalent of a Feisty server install & the Fluxbox Window Manager..... very lightweight, tight & incredibly fast...... even on your 128mb machine you should notice the difference. :)

DJiNN

---

### Post by az on 2007-04-30
> **DJiNN said:**
> 
128mb Ram is fine (

You need 192 megs of ram to boot the live cd and 256 megs to actually run the installer.  Less than 256 megs of ram is not recommended for Ubuntu.

---

### Post by RedSquirrel on 2007-04-30
> **purplearcanist said:**
> Also, I was just guessing at the ram.  I don't know if it is 128 or 256 MB.

I might need to upgrade the computer.


If it is only 128 MB, I would try a barebones install and a lightweight window manager. Here are some instructions to use the net installer (no need for a CD): [Barebones Install]("http://www.psychocats.net/ubuntu/minimal#barebones")

When I did my feisty install, I didn't use the net installer as described in those instructions. I grabbed the [server]("http://www.ubuntu.com/products/WhatIsUbuntu/serveredition") CD, installed that, and then built up the rest of the system from there. 

It's up to you. :)

---

