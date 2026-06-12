---
title: "how do i auto run / boot a program un boot up"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by pxshock on 2007-11-17
Hello folkx

first i should say..i been using linux for a wile, but im no where near “knoledgabe” abot this os, please bear with me.

i want to do a coupple things
i got an OLD box 256Mb ram, 20GB hdd, but its a 233Mhz processor.

I want to have this running as a server and i want to run VNC, and ssh.

I installed debian, with no packages at all, so when my pc boots, i see in black and white “debian login”

i have previously been expirimenting with debian, i know that i dont need a GUI to do things, so i plan to just have this box boot up and auto execute VNC.

VNC requite root access.

Since i dont plan to manually start the applications everytime power cuts or a reboot happens, id like automatically for VNC boot up as soon as i reeboot, without me having to log in as su, then manually everytime typing

vncserver

in the terminal

i know in windows, its way way simple, only one user will boot, and in a folder called startup programs id just drag and drop shortcuts to VNC, or simply msconfig, and do the magic tehre.

If anyone is to suggest that i get gdm, and use gdmsetup, and set auto boot to a user, and add a session, this posses three problems, i still need to auto execute VNC, i need to be logged in as su, and i dont want to have a GUI coz my pc just cant handle it.

Yes vnc(tight) does work wothout the X enviroment, it just shows the terminal...from previous testing

Basically, id like to know how to auto run programs on debian as soon as my computr boots up without me having to touch the keyboard at all.

Id like to know how to do all this from the terminal window.

Thank you in advance

---

### Post by derby007 on 2007-11-17
Try a little reading at: 
[http://initscripts-ng.alioth.debian....ianboot_d1.pdf]("http://initscripts-ng.alioth.debian....ianboot_d1.pdf")
Its informative. Hope it helps.

Ooops, looks like link is broken, try: //initscripts-ng.alioth.debian.org/soc2006-bootsystem/deliverable1/debianboot_d1.pdf 
and put 'http:' at start !

---

