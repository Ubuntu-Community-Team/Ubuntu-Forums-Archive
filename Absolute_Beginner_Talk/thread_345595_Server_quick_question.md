---
title: "Server quick question"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Shinitenshi on 2007-01-24
Well I installed the server side of ubuntu the most stable version... just to check it out some. Well does the server side come with a gui like kde or something or just command base? Is there a way to install gui? 

am tring to install a counter strike server for lan, just a game server. done it before but with mandrake and redhat but never with ubuntu just wanted to check it out but if its just commands then am gona be stuck lmao

---

### Post by zerhacke on 2007-01-24
Ubuntu server distribution is only a command line.  On almost every server there is there's no need for a GUI which would just eat up RAM, CPU cycles, and disk space for no real reason.

If you want a GUI, you should either install a regular Ubuntu, Kubuntu, Edubuntu, or Xubuntu distribution.  Your server software will still work with the GUI.

Either that, or keep your server install and install one of the GUI metapackages.

---

### Post by Iarwain ben-adar on 2007-01-24
Hi there,

Sure you can install a GUI

```
sudo aptitude install ubuntu-desktop
```
gives you Gnome

```
sudo aptitude install kubuntu-desktop
```
gives you KDE

```
sudo aptitude install xubuntu-desktop
```
gives you Xfce


Hope this helps :wink:


Iarwain

---

### Post by Shinitenshi on 2007-01-24
> **zerhacke said:**
> Ubuntu server distribution is only a command line.  On almost every server there is there's no need for a GUI which would just eat up RAM, CPU cycles, and disk space for no real reason.

If you want a GUI, you should either install a regular Ubuntu, Kubuntu, Edubuntu, or Xubuntu distribution.  Your server software will still work with the GUI.

Either that, or keep your server install and install one of the GUI metapackages.

do you know of a command to execute the instalation for the gui? theres no problem with me installing normal ubuntu but just wanted to check out the server side. I know a couple commands to do what i need but I don't know how connect to the network stuff like that. thanks man


edited....................  thnx for the commands ill test them out

---

