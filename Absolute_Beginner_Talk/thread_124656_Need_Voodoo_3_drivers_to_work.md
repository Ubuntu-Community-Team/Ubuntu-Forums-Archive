---
title: "Need Voodoo 3 drivers to work"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by frenzy20 on 2006-02-01
I just downloaded and installed Ubuntu on my old emachine, it has a 500mhz p3, 192mb ram, voodoo3 2000 16mb video card.  It runs ok, but the max resolution I can run is 640x480, I'm assuming its a driver problem.  I downloaded the rpm files, but I don't know how to make them work from there, I read something about converting them to .deb, could someone tell me how to make them work?
Thanks

---

### Post by frenzy20 on 2006-02-02
Bump, this is on the 3rd page.  I really just need a tutorial on converting .rpm file to .deb.

---

### Post by soapyfish on 2006-08-31
use synaptic to locate a package called "alien"  then in a termnal type "man alien" without the quotes and it will tell you how to use the program .......... I used it with success as a linux newbie. So the command is some thing like 

#sudo  alien /home/username/file.rpm  ( or the path the the downloaded file inc file name )   

then list the contents with  the ls -la command and you should see a package with the same name but ending in .deb  :-)

then you can use dkpg-add  to install it  :-)

---

