---
title: "Linux Newb Question: Eboostr?"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by D3M0L1$H3® on 2008-02-26
:guitar:
Allright, so I'm kinda a Linux newb. I've been with Windows my entire life, and have only messed aroung with Macs.
I have a kinda old computer with probably 64Mb of RAM, a 4GB HDD.
I was wondering if Ubuntu would run okay on such a system? I really want it and my friend told me that Ubuntu only took up 2GB, so I could just reformat the HDD, and install Ubuntu, right?

And as for the RAM;
A nice little program called Eboostr is a non-Vista version of Readyboost which allows you to use any kind of portable media device as RAM. Will i be able to use this on Ubuntu? Is there an Ubuntu alternative that I can use?

Thanks, I appreciate the help.

---

### Post by Iehova on 2008-02-26
I think ubuntu needs 256MB of RAM to run a graphical environment. I'd sooner suggest something like Damn Small Linux for such a computer.

---

### Post by savagenator on 2008-02-26
Damn Small Linux
Puppy Linux
or if you want, get a stripped down version of ubuntu, and install openbox or fluxbox or some super light window manager, they only use something like 100mb of RAM

---

### Post by northern lights on 2008-02-26
In the Ubuntu family, there's [Fluxbuntu]("http://fluxbuntu.org/"), which will definitely run on your comp. It uses Fluxbox as its desktop manager, which is way more simplistic than GNOME or KDE.
There's also [Xubuntu]("http://www.xubuntu.org"), running Xfce. It will run with 64 megs, but recommended are 128.

You also could consider [Puppy Linux]("http://www.puppylinux.org") or [DSL]("damnsmalllinux.org").

---

### Post by D3M0L1$H3® on 2008-02-27
DSL seems a little too simplistic for me, but fluxbuntu looks interesting. without going out of their way, can someone tell me what differences there are between ubuntu and flux?
:confused:

---

### Post by eriqjaffe on 2008-02-27
Ubuntu is a full-fledged Gnome-based Desktop Environment that won't run with the system you're describing, Fluxbox is just a Window Manager - far lighter on the resources, but doesn't come with all the bells & whistles of a full DE.

---

### Post by northern lights on 2008-02-28
[Fluxbuntu]("http://fluxbuntu.org/"):
- desktop management: Fluxbox
- icons
- taskbar
[IMG]http://cafelinux.org/OptickleArt/albums/userpics/normal_Fluxbuntu_Clear.png[/IMG]



[Xubuntu]("http://www.xubuntu.org")
- minimum 64 megs, but recommended are 128
- desktop management: [Xfce]("http://www.xfce.org/")
- icons
- bit of eye-candy (drop shadows, transparency)
- panel/taskbar
[IMG]http://www.tcmagazine.com/images/news/Hardware/eeeXubuntu_desktop_01.JPG[/IMG]



 [Puppy Linux]("http://www.puppylinux.org"):
- desktop manager: JWM, alternatively IceWM
- two interfaces: X.org, Xvesa (the latter, since more simplistic, should be your choice, unfortunately)
- ideally 128 megs of RAM, minimum 48 - parts of the system can be run from virtual memory (i.e. from the HDD, not the fastest, obviously)
- unique feature: optional custom LiveCD (choose between 300+ (?) apps)
[IMG]http://magarto.com/blog/wp-content/uploads/2007/10/1191352841450501536_cce1e6be80.jpg[/IMG]



[DSL]("damnsmalllinux.org"):
- featherlight: minimum 8 (!) megs of RAM, 486 processor (this would be ideal, as it allows you to run more than just two to three jobs before your comp slows down)
- nonetheless: icons, taskbar, themes (in other word's a full-fledged desktop environment)
[IMG]http://flaviostechnotalk.com/wordpress/wp-content/dsl12.png[/IMG]

Note: Every one of these distros is customizable, and none of these pictures represent the one and only way that particular distribution can look like. Rather, notice the capabilities of each desktop environment.

Anyways, I'd say DSL is a fair package, considering your amount of physical memory - what are the other specs? (Not that important either. Man, jusy give it a shot)

---

