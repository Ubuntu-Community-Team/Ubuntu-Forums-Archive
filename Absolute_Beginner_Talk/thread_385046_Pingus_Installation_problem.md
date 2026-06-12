---
title: "Pingus Installation problem"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by Lightik on 2007-03-15
I've a problem installing pingus game on Ubuntu 6.06. Help me please. Once I try to install pingus package system asks to install pingus-data package first. Once I try to install pingus-data package system asks to install pingus package first. What a bergmuda triangle. What should I do to install this game? Help me please. I search on the forum and found nothing concerning this problem.  And oh by the way, I try to install it while working in Live CD mode. Is it possible to install the game and play it?

---

### Post by atraeyu on 2007-03-15
Strange.  Are you using the Synaptic Package Manager?  When I installed pingus it told me it needed to install additional packages and automatically included the data package for installation ... of course that's on Ubuntu 6.10 edgy ...

---

### Post by mcduck on 2007-03-15
So you have downloaded Pingus as 2 separate .deb packages? You can install them both at the same time from command line with 'sudo dpkg -i package1.deb package2.deb'.

---

### Post by Lightik on 2007-03-15
Yes, I've downloaded all packages the game requires separetly. Will it work while in Live CD?

---

### Post by mcduck on 2007-03-15
If you have enough RAM then you should be able to install anything, just like if you were running Ubuntu from hard disk. (of course you'll loose everything you installed when you boot the machine)

---

### Post by Lightik on 2007-03-15
> **atraeyu said:**
> Strange.  Are you using the Synaptic Package Manager?  When I installed pingus it told me it needed to install additional packages and automatically included the data package for installation ... of course that's on Ubuntu 6.10 edgy ...

I just double click on the package and and installation begins.

---

### Post by Lightik on 2007-03-15
> **mcduck said:**
> If you have enough RAM then you should be able to install anything, just like if you were running Ubuntu from hard disk. (of course you'll loose everything you installed when you boot the machine)

thanks for response!

---

### Post by Lightik on 2007-03-15
> **mcduck said:**
> So you have downloaded Pingus as 2 separate .deb packages? 

is there a way to download full package? In Ubuntu repository packages.ubuntu.com there are only separate packages. Look here - [http://packages.ubuntu.com/edgy/games/pingus](http://packages.ubuntu.com/edgy/games/pingus)

---

### Post by mcduck on 2007-03-15
> **Lightik said:**
> is there a way to download full package? In Ubuntu repository packages.ubuntu.com there are only separate packages. Look here - [http://packages.ubuntu.com/edgy/games/pingus](http://packages.ubuntu.com/edgy/games/pingus)

well, if you are getting stuff from ubuntu repositories you shouldn't even be downloading them yourself, just use Synaptic (in System/Administartion/Synaptic) or gnome-app-install (in Applications/Add/Remove..) or apt-get from command line..

Here's a nice guide how to install things in Ubuntu: [How to install *ANYTHING* in Ubuntu]("http://cutlersoftware.com/ubuntuinstall/")

---

### Post by Lightik on 2007-03-18
Thanks a lot. Very useful link!

---

