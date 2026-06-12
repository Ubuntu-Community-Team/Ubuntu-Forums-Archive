---
title: "kde and gnome together?"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by sailingboarder on 2007-01-01
is it possible to install say kubuntu, which runs kde, and then install gnome and run the two together, maybe selecting the one i want at startup?

could i do that without having a dual boot ubuntu and kubuntu?

---

### Post by meng on 2007-01-01
Yes, absolutely, start by installing Kubuntu and then drop to terminal:
sudo aptitude install ubuntu-desktop
then you'll have a choice.

---

### Post by kepos on 2007-01-01
install kubuntu, ubuntu or xubuntu and then just add desktops you would like:

gnome: sudo apt-get install ubuntu-desktop
kde: sudo apt-get install kubuntu-desktop
xfree: sudo apt-get install xubuntu-desktop

but they are large, so forget about it if you have slow internet connection

---

### Post by seijuro on 2007-01-01
> **kepos said:**
> install kubuntu, ubuntu or xubuntu and then just add desktops you would like:

gnome: sudo apt-get install ubuntu-desktop
kde: sudo apt-get install kubuntu-desktop
xfree: sudo apt-get install xubuntu-desktop

but they are large, so forget about it if you have slow internet connection

For sure, in fact you better have dsl, cable or better.

*cries in misery over his dialup..*

---

### Post by Tux Aubrey on 2007-01-01
Even cooler (IMHO) is to run alternative WMs in separate X-Sessions (without having to logout).  After you have downloaded and installed the WMs you want, check out bodhi.zazen's script [[COLOR="Blue"]**here**[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=271674&highlight=fluxbox+gnome+kde+xfce").

(Disclaimer: I am not in any way associated with bohdi.zazen Inc. and receive no commission or fee for this endorsement.  Aubrey)

---

### Post by sailingboarder on 2007-01-01
thankyou for the help
i thought it might b that simple, i just wanted 2 check b4 i went ahead with an install

---

