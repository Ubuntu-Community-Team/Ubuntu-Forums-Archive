---
title: "Desktop or Server"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by makko on 2008-01-04
I am going to go at ubuntu again but am unsure which version to go for.

6.06 Desktop GUI or 6.06 Server CLI

If i go down the server route it will be all command line right? But am I right in saying that x windows will bring some graphics to this so i can browse the net or open up a graph to display web stats etc?

I'll be running it on a 700mhz pentium with 384mb RAM.. I've had the desktop version on a similiar pc but it ran sluggish enough.

Thanks,

Makko

---

### Post by LowSky on 2008-01-04
Your processor is a little slow for ubuntu but you have enough RAM to Run Xubuntu if you want a GUI.

---

### Post by charlie763 on 2008-01-04
You may consider doing a server installation, which should result in a command line only system. You'll also have all the server goodies installed right away. You can always install the Ubuntu desktop by typing
```
sudo apt-get install ubuntu-desktop
```
at the command line.

---

### Post by makko on 2008-01-04
I see.. Can I install xubuntu from the command line Charlie?

Also is my computer too slow for ubuntu server aswell? I thaught it was the gui that was slowing the whole thing down.

What kind of goodies will I get from the word go?

---

### Post by jba6511 on 2008-01-04
what do you plan to use the pc for? are you hosting shares, domain controller, etc.? If this is just for general use (ie web, email, etc.) use the desktop and look at xubuntu due to your system specs.

---

### Post by makko on 2008-01-04
I plan on using it as a home server initially and then a web server.. no real need for graphics. I am just worried at only having a command line and no graphics but I suppose it's the best way to learn the commands,yes?

---

### Post by barbedsaber on 2008-01-04
in generall, the newer versions work better (faster) 
my point is ubuntu 7.10 or xubuntu 6.06...
maybe
not neciserly
maybe

EDIT I think I am wayh out of my depth,

---

### Post by charlie763 on 2008-01-04
Check out the development of the [Ubuntu Home Server project]("http://ubuntuhomeserver.org") 

You can sudo apt-get install any of the following desktop environments:
edubuntu-desktop
edubuntu-desktop-kde
gobuntu-desktop
ubuntu-desktop
kubuntu-desktop
xubuntu-desktop

I don't know exactly what you get from a server install, but you could start by reading the [Ubuntu Server Guide]("http://doc.ubuntu.com/ubuntu/serverguide/C/").

As far as speed, I think you'll be fine. I'm running a site of a lower spec computer without any problems. Take a look at [http://www.openphysics.org/~gladex/](http://www.openphysics.org/~gladex/) and [http://www.openphysics.org/](http://www.openphysics.org/) to see what a 500 MHz PIII can do.

---

