---
title: "Installing xubuntu desktop on Edgy server"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by PetePete on 2007-06-12
I want to install XFCE on my edgy server, currently it is just CLI only.

what packages do I need to install?
xubuntu-desktop ??

If i install that, will it boot straight into the login manager GUI, or do I need to install a seperate package for that?

I've just ran a simualtion of installing xubuntu-desktop and it installs ALOT of not required stuff.
is there a package for just the X server and XFCE required files?

---

### Post by PetePete on 2007-06-12
sorry please ignore this thread.

decided against installing xfce, got other plans now ;)

cheers

---

### Post by guysmiley25 on 2007-06-12
In theory it should work however I have had problems, I would recommend doing it like this.

```

sudo aptitude install xorg
sudo aptitude install gdm
sudo aptitude install xubuntu-desktop

```

The only other problem I've come across was due to GDM some how logging into Xfce without it being a Xfce session. To make sure this does not happen, when you first login make sure you select xfce as your session type.

Good luck.

---

### Post by pxwpxw on 2007-06-12
xfce4 is a meta package in the multiverse or universe (forget which)
then xorg is another  to privide the x windows bit. Might be a few loose end to install.

 aptitude search xorg.

fluxbox is a good desktop, theres a howto somewhere, it also comes in one package.


xorg
xfce4
fluxbox

debian forum has a lot of threads re minimal desktops.

---

### Post by guysmiley25 on 2007-06-12
Oh after all that, Oh well.

Good luck anyways!

---

### Post by PetePete on 2007-06-12
thanks, but i've changed my mind back again lol

i'm doing this because I want to setup x11 forwarding over the internet so i can run my apps from anywhere.

would it be possible to just install xorg and say firefox or what ever apps i require?

sudo apt-get install xorg enlightenment firefox

---

### Post by pxwpxw on 2007-06-12
Yes I did run firefox once on just X windows, it is possible, cant move it around though.

---

### Post by DonnieP on 2007-06-12
If you install the Synaptic package 'xfce4' rather than 'xubuntu-desktop' you'll get just what you need without all the apps you may not want (like Abiword and Gnumeric).  I just recently installed this package on top of Ubuntu Feisty and use the sessions option during login to select it.

---

