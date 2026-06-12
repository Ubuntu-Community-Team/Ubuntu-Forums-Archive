---
title: "Is This a Viable Server Setup?"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by LeAstrale on 2007-12-11
Hi there.

I just recently bought and old server from a friend, i dont know what he used it for, but i do know that it has windows server 2000 on it.

The specs is as following:
2,8GHZ Celeron
256 MB RAM
a total of 900GB disks as follows:
3x200GB IDE disks
1x300GB SATA 150 (sitting in a HDD tray)
1 very expensive 8x port IDE controller (approx. 2000$)

1. Is Ubuntu server edition able to run on this? (with GUI)

2. Which GUI would you recommend for the job? (NOTHING flashy needed!)

3. Several places i can see that for lower end systems there is a (somewhat) huge gain by compiling your own kernel and disabling all unneeded daemons and services, is it needed and how much would it mean to a system low on RAM ?

4. Is there anything more i should now when the server is to be used as a file server and connects to windows XP macines?

Thank you for you time everyone.

BTW. i bought the machine for 100$ :)

/LeAstrale

---

### Post by jaybombalous on 2007-12-11
Server as in how?

y the IDE drives? I would have just bought all SATA or scisi and setup raid. :(

---

### Post by SupaSonic on 2007-12-11
Well, I recently set up a debian server, which should be close to ubuntu server. Without gui it peaked at 45 MB RAM with samba, cvs and mysql. With Gnome it was maybe 145 - 155 MB. So yeah it'll work just fine I think.

---

### Post by LeAstrale on 2007-12-11
> **jaybombalous said:**
> Server as in how?

y the IDE drives? I would have just bought all SATA or scisi and setup raid. :(

Server as in file, storage and backup server. its and rather old PC and i didnt choose the hardware myself (note the price)

however if the rather expensive IDE controller is working under Linux it should be able to make the 3 IDE disks run in RAID.


#3: Is it possible to just "take down" the GUI when everything is setup and installed? and what did you use the server for?

---

### Post by jaybombalous on 2007-12-11
> #3: Is it possible to just "take down" the GUI when everything is setup and installed? and what did you use the server for?

u asking the wrong person about this, but in theory u can set it up and then remove everything including the screen and just use a ssh session to do any sort of work on the machine remotely. This ought to save on memory usage. :)

---

### Post by Xbehave on 2007-12-11
> sudo killall Xorg 
will kill the GUI
alternatively most GUI will let you login to a console which i think stops Xorg nicely
once there you can uninstall Xorg
configure it not to boot automatically
break your xorg.conf


Ive heard that if the server is pointed to the outside world you should definatly not use Xorg, just removing the monitor isnt good enough

---

### Post by Existentialist on 2007-12-11
That should be more than enough to run a file server.  I have ran an smb server on a 450mhz p3 128mb ram, with about 10 machines connected to it without a GUI.  Your machine should be more than capable of running gnome and x, but to conserve resources, I would consider running xubuntu as it is designed to run on computers with only 64mb of ram minimum.  Either way you can go back in and delete the desktop package after you get everything set up, or disable it from starting in the sessions menu.  I believe with xubuntu you just remove that xubuntu-desktop package to get rid of the it.

If you are going to run the ubuntu server edition you could run a GUI like xfc or fluxbox for a really light weight windows manager.

If this is purely a file server, and you are running it on a private network there is not much you have to worry about, but if it is accessible from outside of your network, or you only want to allow certain computers to connect, you may want to consider setting up rules in iptalbes to only allow certain ips or mac addresses.

---

### Post by LeAstrale on 2007-12-12
> **Existentialist said:**
> That should be more than enough to run a file server.  I have ran an smb server on a 450mhz p3 128mb ram, with about 10 machines connected to it without a GUI.  Your machine should be more than capable of running gnome and x, but to conserve resources, I would consider running xubuntu as it is designed to run on computers with only 64mb of ram minimum.  Either way you can go back in and delete the desktop package after you get everything set up, or disable it from starting in the sessions menu.  I believe with xubuntu you just remove that xubuntu-desktop package to get rid of the it.

If you are going to run the ubuntu server edition you could run a GUI like xfc or fluxbox for a really light weight windows manager.

If this is purely a file server, and you are running it on a private network there is not much you have to worry about, but if it is accessible from outside of your network, or you only want to allow certain computers to connect, you may want to consider setting up rules in iptalbes to only allow certain ips or mac addresses.


The Server might in the future be accessible from the outside, but setting up iptables with the corresponding mac adresses shouldn't be that hard. 

Which GUI is the best for this lightweight operation?
Fluxbox?
XfCE?
Enlightment?
or some other?

Thank you for your time

/Astral-1

---

