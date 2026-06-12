---
title: "No Graphical Interface upon install"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by muymalestado on 2007-07-03
Others have been advised here, but I cannot succeed with the methods suggested.  After clean install on to whole HDD (AMD machine) of Ubuntu Server 7.04  (fiesty?) I am in the terminal.  I believe I installed Standard instead of Desktop, by mistake.

Where does one find the graphical interface files?

Thanks

---

### Post by caffienefree on 2007-07-03
sudo apt-get install x-window-system-core gnome-core gdm

---

### Post by muymalestado on 2007-07-03
Thanks caffienfree - after entering as instructed at the $ prompt I get :-
E: Couldn't find package x-window-system-core

---

### Post by Malibu Illusion on 2007-07-03
```
sudo aptitude install ubuntu-desktop
```

---

### Post by muymalestado on 2007-07-03
Thanks Malibu

After asking for password - Building, Reading and Initializing started.

Then - Couldn't find any package whose name or description matched "ubuntu-desktop"

So nothing gained

---

### Post by jdrodrig on 2007-07-03
Just wondering,
do you have internet connection?

---

### Post by muymalestado on 2007-07-03
Thanks jdrodrig

You guessed it - I was hoping to get this box working stand-alone prior to connecting - so now I have connected (a wire) to the router and I suppose the game is to configure a gateway and enable DHCP.

There may be a case to start the install from scratch to see if that will ask for requisite parameters.

As to the original problem of No desktop I guess from what you ask that these are found on internet sites by the ubuntu system.

---

### Post by jdrodrig on 2007-07-03
Prior to connecting? Don't worry, it has happened to many (including me)..LOL.

As I understand it, each LiveCD (desktop) has the corresponding desktop GUI package (ubuntu=gnome,kubuntu=kde, etc...), but the server edition may very well come with none of them so that you would need to download. The good news is that a command as simple as sudo aptitude install ubuntu-desktop can do all the work for you...

If you have problems configuring the dhcp by hand, you may want to do a fresh intall of Ubuntu desktop and then just search how to turn off the GUI whenever you only need the server functionality.

---

### Post by muymalestado on 2007-07-03
The fresh install whilst connected is in progress.  

Thanks

---

### Post by caffienefree on 2007-07-03
The command that I gave you is for a minimalist gui, which I assume you want since you installed the server package. Installing either the ubuntu-desktop package or the ubuntu desktop edition will give you a lot of software that isn't required for a server. You'd be better off just editting /etc/network/interfaces to contain the following:

auto eth0
iface eth0 inet dhcp

then issuing sudo ifdown eth0 and sudo ifup eth0

---

