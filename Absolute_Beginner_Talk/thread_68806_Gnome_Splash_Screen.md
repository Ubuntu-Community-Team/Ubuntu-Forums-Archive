---
title: "Gnome Splash Screen"
date: 2005-09-24
forum: Absolute Beginner Talk
---

### Post by blathum5 on 2005-09-24
Hi there this a noob question so please don't Laugh too much.  I want to change the resolution of the Gnome login screen.  For some reason it will only run at 1280 x 1024 which is a little too much for my 14" monitor.  Better still I would prefer just to boot to the console and start X manually.  My primary function for this machine is a file server.

---

### Post by kassetra on 2005-09-24
[QUOTE=blathum5]Hi there this a noob question so please don't Laugh too much. I want to change the resolution of the Gnome login screen. For some reason it will only run at 1280 x 1024 which is a little too much for my 14" monitor. Better still I would prefer just to boot to the console and start X manually. My primary function for this machine is a file server.[/QUOTE]

Since you want to just start X manually, I'll give the instructions to disable gdm.
Open a terminal and first determine your runlevel:
 ```
runlevel
``` (Mine says N 2 - which means I'm in runlevel 2)
Next, you'll need to remove a symlink to gdm for the correct runlevel:
 ```
cd /etc/rcN.d
``` (N = your runlevel number, in my case, /etc/rc2.d)
You'll want to find the link with gdm in it: 
 ```
ls *gdm
``` (mine said S13gdm)
Now you'll want to remove that link with sudo:
 ```
sudo rm S13gdm
``` (remember to substitute your link name here, I'm using mine as an example.)

When you reboot, you'll be dumped into a terminal window until you type startx.

---

### Post by blathum5 on 2005-09-24
hi there thanks for the tip kassetra

Can't seem to find the /etc/rcN.d in my /etc/ directory mmm seems a little strange I do have a /etc/rcS.d.  I can see the S13gdm in the etc/rc2.d.  Is there a work around for this again thanks for the tip hope you can help further.  I am running 5.04 Horey the Hedgehog.

---

### Post by fordfan753 on 2005-09-24
N just means whatever **N**umber run level you are in. Which in your case is 2. Kassetra said this somewhere in the post, you must have just skipped over that bit a little too fast, re-read it and I think you'll get it. ;)

---

### Post by blathum5 on 2005-09-24
Hi there kassetra 

I got a little head strong and just removed the S13gdm from the /etc/rc2.d all is ok no more login screen.  I guess at the moment that was my only real hate of Unbuntu.  I once was a slackware user but Unbuntu is such a cool OS.  Thanks so much for your help really appeciated.

Kind regards

Paul

---

