---
title: "Where is my window manager?"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by waynehapp on 2007-05-20
I just installed server 7.04 on my machine. (Gateway GT5408 - NVidea card I think)  When I reboot, I get an ASCII terminal interface. No GUI interface at all, just a command line. I login and I'm staring at a UNIX prompt.  I was expecting some kind of GUI interface.

I did not see anything in the install instructions to suggest that some additional action is required to get a GUI interface running. 

Whay could be wrong or what am I foing wrong?

My machine is connected to a wireless network acceess point which in turn is connected to a wireless router and cable modem.

Wayne

---

### Post by aysiu on 2007-05-20
The Server edition doesn't install a GUI.

Log in first.

If, for some reason, you feel you need a GUI to administer a server, try this: ```
sudo apt-get update
sudo apt-get install xorg icewm menu gksu synaptic xterm rox-filer
startx
``` If you don't want a server but really want a home desktop, do this instead: ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
```

---

### Post by bobplano on 2007-05-20
for security purposes and to run better there is no default GUI for the server install. to add a GUI do 
```
sudo aptitude install ubuntu-desktop
```
just replace ubuntu with kubuntu or xubuntu depending on if you want gnome, kde, or xfce.

---

