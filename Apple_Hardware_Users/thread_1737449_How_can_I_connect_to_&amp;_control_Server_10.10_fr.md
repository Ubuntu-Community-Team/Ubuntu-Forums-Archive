---
title: "How can I connect to &amp; control Server 10.10 from an iMac"
date: 2011-04-23
forum: Apple Hardware Users
---

### Post by Elric58 on 2011-04-23
I have installed Ubuntu Server 10.10 on a PC which is connected to my home network.  I want to be able to connect to this PC from my iMac (OS X 10.6) and run things remotely like I can do with software such as VNC between Windows systems.  Thanks in advance.

---

### Post by cellarweasel on 2011-04-24
Elric, you need to decide which method you want to use. There are three that I use. The simplest is to do(in the terminal):```
ssh *username@ubuntuhostname*
``` This gives you basic shell access. Which may not be as good as a GUI. The second two methods are to use VNC or X desktop forwarding which will give you the full GUI. 

For VNC unfortunately Mac OS X.6 doesn't come with a VNC client so after turning on the VNC server on ubuntu you will also have to download a client. Sorry I don't have a regular Ubuntu in front of me but regular Ubuntu (I'm using Xubuntu) comes with the server by default, and I remember it as not being that difficult to allow other machines to access it. 

The third method is a bit wonky but works pretty well. What you can do is create a terminal to your linux box from your mac. I actually know how to do this off the top of my head. You first open X11.app from the utilities folder, same as where terminal.app is, and in the xterm it opens you do ```
ssh -XY *username@ubuntuhostname*
```  and then you can start GUI apps that are running on your linux machine on your mac desktop. This includes the entire Gnome/KDE desktop if you want. For KDE the next command you would type would be ```
startkde 10:0
``` this will start kde on your already running mac desktop, for gnome it's ```
startx 10:0 ; metacity ; gnome-session
``` Or at least that is what I remember working. It will be kinda weird seeing two desktops running hybrid style but whatever. Also if 10:0 gives you and error you need to figure out your mac's display number. 

Hope that gives you some ideas and stuff to try.

---

