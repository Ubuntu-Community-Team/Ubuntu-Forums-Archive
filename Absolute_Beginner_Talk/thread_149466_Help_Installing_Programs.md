---
title: "Help Installing Programs"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by GhandiBurger on 2006-03-23
I have been using Ubuntu for about a month but can't do much except surf the net. I would like to know how to install programs in Ubuntu that you have downloaded. Any help on installation would be awesome.

---

### Post by KansasJoe on 2006-03-23
Depends on the program...you can

sudo apt-get install programname

dpkg -i packagename.deb

./configure
make
sudo make install

some programs simply run with ./setup...hard to say unless you tell us what program it is

---

### Post by GhandiBurger on 2006-03-23
I need to install Nvidia drivers for my graphics card. Also, is there a way to do it in the graphic interface? Or only in the terminal?

---

### Post by aysiu on 2006-03-23
System > Administration > Synaptic Package Manager

---

### Post by GhandiBurger on 2006-03-23
Aye, but where is the package/how do I put it where it needs to be?

---

### Post by icyisamu on 2006-03-23
[QUOTE=GhandiBurger]Aye, but where is the package/how do I put it where it needs to be?[/QUOTE]

After you install it via synaptic, you don't need to worry about the rest. The system will deal it for you.

---

### Post by aysiu on 2006-03-23
You need extra repositories for that:

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then, this tutorial should help you use Synaptic:

[http://www.psychocats.net/essays/winuxinstall](http://www.psychocats.net/essays/winuxinstall)

---

### Post by GhandiBurger on 2006-03-24
Thanks for that. I managed to install nvclock which is an nvidia overclock program, but I can't get that to open. It says I need to have official nvidia drivers. I have these installed
Non-free Linux 2.6.12 modules on 386
NVIDIA binary XFree86 4.x/X.Org driver
NVIDIA binary kernel module common files
Tool of configuring the NVIDIA graphics driver
X.Org X server -- NV driver

---

