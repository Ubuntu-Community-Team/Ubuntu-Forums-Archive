---
title: "LAMP install on desktop"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by smakb on 2007-02-06
Just trying to get my head around Ubuntu (normally maintain windows network) to set up a Moodle server.  I installed the Server LAMP version, but could no find my way around to do much else, Now I have installed the Desktop version, and set it to not run the GDM unless specified, this way I sould get good performance but helps me find my way around.

How should I go about installing AMP (Apache, Mysql, PHP)?  can this be done as a group install from the Server disk? or would I be better to reinstall Server LAMP and put Gnome on top to help me find my way around?

Would like to use a clean Server LAMP install, but unless I can secure, maintain, backup to tape and restore data, I don't see how I can do that.

Thanks

Hopeless 
:confused:

---

### Post by Hanzerik on 2007-02-06
The way I did it was to install the LAMP server, then install xserver-xorg-core and Fluxbox. This is about as minimal as you can get.

If I need to fire up a Windows manager, I just type startx. But I do most of my work remotely so I use SSH and VNC when needed.

.xinitrc
```

startfluxbox &

```

---

### Post by smakb on 2007-02-06
Thanks for the info, but a question for some who has issues (my brain does not work). How do I install xserver-xorg-core and Fluxbox.

---

### Post by Hanzerik on 2007-02-06
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install xserver-xorg-core Fluxbox

It will run through and install any dependences that these packages require, then ask if you want to install them, hit y and then enter.

---

### Post by smakb on 2007-02-06
Thanks.  very much appreciated

---

### Post by bikeboy on 2007-02-06
Same goes for installing the AMP parts on your desktop install.

sudo apt-get install apache2 mysql-server mysql-client php5

When you have the GUI on, you can also install things through System > Admin > Synaptic Package Manager.

---

### Post by smakb on 2007-02-07
I Tried those commands. It reports that it "Couldn't find package"  ANy ideas?

---

### Post by bodhi.zazen on 2007-02-07
1. You need to enable a few repositories:

[http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

Then sudo aptitude update

Then install

2. Another option is Fluxbuntu. Fluxbuntu is a fairly light weight install with Fluxbox already installed.

You can add your server programs as needed.

[Main page](http://fluxbuntu.org/)

[forums](http://community.fluxbuntu.org/)

[ Download fluxbuntu-nbuild1-rev2-desktop-i386.iso](http://modzer0.cs.uaf.edu/~hardwarehank/fluxbuntu/rev2/fluxbuntu-nbuild1-rev2-desktop-i386.iso)

MD5SUM  : 
	> c054428c46a1b5ffaab4295bc7db3c9b  fluxbuntu-nbuild1-rev2-desktop-i386.iso

---

