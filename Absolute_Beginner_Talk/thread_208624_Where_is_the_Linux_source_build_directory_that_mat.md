---
title: "Where is the Linux source build directory that matches your running kernel?"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by Kiddalee on 2006-07-03
I don't know!  Is it a part of build-essentials, or am I supposed to download something?  Not having this thing is a pattern in the errors I've gotten when trying a multitude of ways to fix my Winmodem.
Is it normal for all of my drivers and everything I try to be whining about not finding /usr/src/linux?

---

### Post by az on 2006-07-03
[QUOTE=Kiddalee]I don't know!  Is it a part of build-essentials, or am I supposed to download something?  Not having this thing is a pattern in the errors I've gotten when trying a multitude of ways to fix my Winmodem.
Is it normal for all of my drivers and everything I try to be whining about not finding /usr/src/linux?[/QUOTE]
sudo apt-get install linux-headers-386

---

### Post by golfbuf on 2006-07-03
[QUOTE=Kiddalee]I don't know!  Is it a part of build-essentials, or am I supposed to download something?  Not having this thing is a pattern in the errors I've gotten when trying a multitude of ways to fix my Winmodem.
Is it normal for all of my drivers and everything I try to be whining about not finding /usr/src/linux?[/QUOTE]

Yes, build-essential, and linux-headers-386 and their dependencies are all on the install CD, but are not installed by the default installation.  So, you need them for building things like a modem driver.  Alien, and fakeroot are also useful and on the CD.  This should get you going.

But, there are many other developement packages that you will need to build x11, kde or gnome software, so you'll eventually have to download that stuff when you need it later.

HTH,

---

### Post by Bloch on 2006-07-03
Enter 
uname -a
to see what kernel you are running. 
Open synaptic. Click Settings --> Repositories and make sure those with Source are ticked.
Then search in synaptic for your kernel and install the source.

But recompiling the kernel source is not a beginners kind of thing. Winmodems are notoriously difficult. 

You can buy an internal modem card for $14. You might even be able to get one free from some junk computer.

---

### Post by Kiddalee on 2006-07-03
Temporary failure resolving "security.ubuntu.com"
I don't have my modem working yet.  That's what I've been trying to do, and it would be quite ironic if I needed to have an internet connection in order to make it possible to run my driver.
As for the things that did install okay, are they sufficient to get my driver working?

---

### Post by Kiddalee on 2006-07-03
Thanks.

[QUOTE=Bloch]You can buy an internal modem card for $14. You might even be able to get one free from some junk computer.[/QUOTE]

I'm running a Notebook, and I'm not hardware savvy.  Would this still be decently easy?

---

### Post by T700 on 2006-07-03
[quote=Kiddalee]I'm running a Notebook, and I'm not hardware savvy.  Would this still be decently easy?[/quote]

Generally, no.  Notebooks are often very tough to upgrade.  You might consider an external modem, if you don't mind giving up some convenience.

Paul

---

