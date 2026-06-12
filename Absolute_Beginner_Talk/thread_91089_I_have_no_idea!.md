---
title: "I have no idea!"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by inovermyheadd on 2005-11-16
Ok so I downloaded xmoto-0.1.8-src.tar.gz

and I have no idea what to do with the file...I tried to find it on wiki...but I got lost....I did use it to install some packages of games that I guess I had on my computer all ready?  This is going to take some getting used to!

Anyway, Thanks!

---

### Post by KingBahamut on 2005-11-16
Source installation file. 

Basically 

guznip xmoto-0.1.8-src.tar.gz
tar -xvf xmoto-0.1.8-src.tar
cd xmoto-0.1.8
./configure 

if configure fails, meet the dependencies it asks for 
if configure succeeds.....

make
sudo make install

---

### Post by inovermyheadd on 2005-11-16
[QUOTE=KingBahamut]Source installation file. 

Basically 

guznip xmoto-0.1.8-src.tar.gz
tar -xvf xmoto-0.1.8-src.tar
cd xmoto-0.1.8
./configure 

if configure fails, meet the dependencies it asks for 
if configure succeeds.....

make
sudo make install[/QUOTE]

cool!  now what do I do with this file...gtkpod_0.94.0-1_i386.deb

---

### Post by aysiu on 2005-11-16
You don't have to download the Gtkpod .deb separately.
Enable extra repositories (see my sig), then just type this in a terminal ```
sudo apt-get update
sudo apt-get install gtkpod
``` The .deb and all its dependencies will be downloaded and installed all at once.

For more info on the different ways to install software in Ubuntu, read [this](http://www.psychocats.net/linux/installingsoftware.php)

---

