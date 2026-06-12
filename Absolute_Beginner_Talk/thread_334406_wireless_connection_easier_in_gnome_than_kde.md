---
title: "wireless connection easier in gnome than kde"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by sailingboarder on 2007-01-08
when i ran gnome in dapper drake, wireless connection was easy
it automatically connected to the house network upon startup, and would reconnect if the network went offline then back online

under kde, with edgy, wireless is alot more painful, well in comparison
instead of having the always on feel that gnome had, i have to remember to navigate through the menu's to the Wireless Assistant Wireless LAN Manager, and then connect to the network

is there a way to make kde connect automatically like gnome did?

---

### Post by aysiu on 2007-01-08
I believe you can actually use *network-manager* in KDE. I'm not 100% sure about that, though.

---

### Post by MkfIbK7a on 2007-01-08
i used kde and yes you can use network manager...

---

### Post by sailingboarder on 2007-01-08
is network manager the program gnome used? or is it something else?

---

### Post by MkfIbK7a on 2007-01-08
well gnome can use wifi-radar or network-manager...

---

### Post by sailingboarder on 2007-01-09
i installed network-manager through Add/Remove Programs
but now i can't figure out how to make it work
i can't find it in the menu's or by searching my computer

how do i start it and use it in kde?

---

### Post by Sef on 2007-01-09
Try alt+F2.  That should bring up the Run Application manager.  Just type in network-manager to get it to run.

---

### Post by sailingboarder on 2007-01-09
sometimes i wish i would look harder before posting here

looking through the repositories just to check that network-manager was installed, i found knetworkmanager, a kde front end for the program

so after installing that package, it works perfectly, just like in gnome

y does this program not come default with kubuntu instead of the Wireless LAN Manager?

---

### Post by jchapman on 2007-02-27
I installed the KDE set on Ubuntu the other night (not the entire Kubuntu desktop, mind you) and then followed the advice here and installed knetworkmanager. It showed up for a moment, looking just like its Gnome counterpart and then proceeded to error out on me. It sat in the top toolbar with a red "x" over it proclaiming it wasn't running. Nothing I could do would enable it to run and, to make matters worse, it seemed to have replaced my Gnome network-manager applet!

Long story short, I was able to regain my Gnome network-manager (notice the "-" is the distinction between the KDE and Gnome variety of this app) by reinstalling it. My experimentation with KDE is thus over and that environment has since been removed. Nothing beats Gnome for ease of use and for font rendering!

---

### Post by aJavaCoder on 2008-04-14
I had this problem after switching from Gnome to Kde, then I just used the same program as gnome which is nm-applet.

If you run nm-applet the wireless icon should appear like in gnome!

N.B. if you have open an other wifi like Kwifi or something like that close it and put your nm-apple wireless configurationt to autodetect mode. (the check box).

---

