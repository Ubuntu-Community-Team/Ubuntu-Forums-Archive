---
title: "Cannot install any .deb files"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by rafucho on 2006-02-17
Well here's the thing, I'm running Breezy, and I love it, the pity: I don't have a permanent network connection, so, I don't internet acces, i want to learn a lot, but I can't, I want to install things and I also can't. I have a wireless pci-card, and windows runs just fine with it. I want to install it, but the command

sudo dpkg -i file.deb

doesn't find anything, it doesn't install anything, I have ndiswrapper, and beep media player in deb files, and I can't install them. I tried everything, but I can't to anything because of the net... since apt-get works just fine, but the deb files don't. As soon as I can install my wireless I'll have net access, but since I can't install ndiswrapper, can't do anything yet, could you please help me?
sorry 'bout my english, I'm from Colombia, and it's has been a while, since I don't practice.... bye
thanks

---

### Post by kaamos on 2006-02-17
Ndiswrapper is in the install cd. Just use synaptic to install ndiswrapper-utils.

---

### Post by ewtesterman@cox.net on 2006-02-17
1  Open synaptic and search for ndiswrapper (in 5.10 ndiswrapper is installed already)
2 install ndiswrapper utils using synaptic
3. go to the terminal
4 type " sudo -s " then enter your password
5 put in the cd that has the driver for your wifi card
6 type in the terminal " ndiswrapper -i /media/cdrom0/whatever your driver file is .inf
7 should say forcing install
8 type ndiswrapper -l
9 it should read " driver present, hardware present"
10 if it does type " ndiswrapper -m "
11 now type " modprobe ndiswrapper "
12 almost there now type " gedit /etc/modules
13 this should open a window at the bottom of the list type " ndiswrapper " save and close
14 now go to networking under the system menu and configure and activate your card.

This should get you to the internet.

---

### Post by foxpertise on 2006-02-17
I'm also new to Linux and Ubuntu in particular and just recently came across gdeb.  Install it and use it thus

gdeb --info file.deb

It will give you info about the package and the option to install it

HTH

---

### Post by rafucho on 2006-02-18
thanks for everything, as soon as I'm home I'll try everything

---

### Post by rafucho on 2006-02-23
I'm happy, I'm enjoying Ubuntu, my windows just went out, I dunno why, but it crashed... I'll try to fix, in the meantime I'll be running on ubuntu

---

