---
title: "Problems with Ubuntu will soon go back to windows"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by SpinningAround on 2007-10-28
Well started using ubuntu as I though it was a good thought to use a other OS that "is" more secure and quite easy to run, but the problems simply keep coming with every new thing you try :(

First not the major things mostly what you would get when starting with a totally new system, even if I have a little experience with Linux before. Problem is with Linux possible because there is no standard and simply so many dists, feels like there is very little "this will work". If you look at windows is there usually a package that you simply can install and it's the latest version, I don't see the same thing in Linux and I can't really say you can blame the programmers since there is no dist where you can release a package to then have a source code for the others, think this would make things better for beginners. The good thing is that it's good for security I guess.

The "simply will run" is quite good with ubuntu even maybe better then windows problem is that if you would like to do some changes or configure it a little do the difficulty go throw the roof. 

The problem I have atm that I hope will get fixed sooner or later is the firewall, I really like to have some control over the security. I started out with firestarted and sadly did crash but worked ok but lacked the control i was looking for so I went over to Guarddog that is for kde but can run on gnome so i tried it out and it worked quite and got the settings I'm looking for problem is after working with it and getting some error that I think is related to that i run it in gnome.

So now am I only able to connect to ubuntu wiki but unable to reach google or wikipedia even if I allowed port 80 and ftp, miss a setting saying "settings for web browser" and similar and sadly isn't the torrents working either. So is my next step to learn iptables? :confused:

EDIT:
Forgot to add maybe the most important since I have worked with the firewall can't I now update the program list in synaptic.

Sorry for a the little angry tone but think you know how things become when you think.
*Why isn't it working, it SHOULD work!?*

---

### Post by kellemes on 2007-10-28
Guarddog is **not** for KDE.
It's gui is based on QT but who cares.. It's unimportant and has nothing todo with the firewal itself.
If you simply turn-off your firewall (in Guarddog it's one checkbox away) you should be able to connect and find support if you can't figure out how to set Guarddog up.

---

### Post by Pumalite on 2007-10-28
Ubuntu comes with all ports closed by default. So, you already have a firewall. Everytime you use a program that uses a port, it forwards one. (I had no problems with Ktorrent). In fact in ubuntu you don't need a firewall. That's Windows mentality. If you are that paranoid, get a router; that's a real firewall. What you have is a bad installation and/or lack of patience to learn a new system.

---

### Post by steve.horsley on 2007-10-28
> **Pumalite said:**
> Ubuntu comes with all ports closed by default. 

Unfortunately, it doesn't any more. It installs by default with UDP ports 5353 and 32768 open. These are opened by the process avahi-daemon. You can see this with the command **netstat -planu**

---

### Post by runemaste644 on 2007-10-28
I tried ubuntu and learned how to do most basic and intermediate operations in a week. I have some problems too, but i managed to fix every one, no matter how hard i screwed up.

---

### Post by SpinningAround on 2007-10-28
Thanks for the reply s :)

Maybe i'm a little paranoid since i already got a router that is quite secure I think :P but since I need to setup a port for the bit torrent is there a little hole in the wall, but is it still safe is the port isn't going to any other program then the torrent program?

A other thing what do I need to enable to get samba working in guarddog?

EDIT: atm I need to go throw the terminal to get the root working if I throw the menu can't I change anything since i'm not root, any solutions?

---

### Post by Pumalite on 2007-10-28
If you are using a router and Guarddog; you are using suspenders and a belt. I didn't understand your question well, but maybe what you need is sudo nautilus.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

