---
title: "Linux noob q possibly"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by geralddean on 2007-08-06
Hey so I have used the live CD for a little while off and on and liked Ubuntu.

While was searching for a version that I could install on my thumbdrive, I decided rather than doing that...that I should dedicate an aging laptop to the quest of expanding my knowledge on linux.

Ubuntu Server Fiesty Fawn is what I have chosen. I chose this because I come from a WAMP environment and wanted to eschew the b$ of m$ and go total LAMP. Anyway...

I dl'ded the image and burned it effectively, and got it installed well enough on my laptop to be able to execute some commands in BASH. But this is the problem (or is it)... I don't see the desktop that I have come to know from the live CD.

There is no GUI, and I'm workign directly from a command prompt. The only application I have run is VI. 

Is this what running Ubuntu server edition entails? Am I or did I neglect to do something in the otherwise straightforward installation?

Please Advise...
humbly,

noob

---

### Post by proalan on 2007-08-06
the server version doesn't come prepackaged with graphical desktops,

I've not tried the server version myself but perhaps the following might install a Desktop GUI for you assuming you have xserver installed. And you have the universal repositories added to your source list.

```
 sudo apt-get install ubuntu-desktop
```or 
```
 sudo apt-get install kubuntu-desktop
```or 
```
 sudo apt-get install xfce4
```the server version is supposed to be lightweight used mainly for, well server/web services.

I think you'd be better off installing the desktop version if you are planning to use your computer primarily as a desktop. You can still install the web services afterwards.

---

### Post by geralddean on 2007-08-06
I figured as much (regarding lightweight versions).
However, I was mainly sold on this version due to the fact that I could be running LAMP right after installing.

I don't mind installing the AMP part though configuring might be an issue, who knows... 

But I kind of wanted the lightweight OS aspect without losing the GUI. I don't know if that is an oxymoron.

Another issue is raised on installing the desktop for the server edition, I'm sure I have to have network connectivity in order to do this. During set up, my network was not configured. How will I address this if say I brought this thing to Starbucks to sudo apt-get install ubuntu-desktop?

All I want this thing for is web development.

---

### Post by proalan on 2007-08-06
for web development the destop version is the way to go, it contains image manipulation tools, editors, browsers...  the lot.

The server edition is suited to hosting the actual sites rather than development work.

Yes you do need access to the internet to install packages. Wireless can be tricky to set up depending on your hardware. I found using a cross over cable connected to another computer/network that is sharing its internet connection the easiest way to go as you don't need to worry about installing drivers.
Once you have a working connection the web services package installation is just as simple as...

sudo apt-get install apache2
sudo apt-get install mysql

and if you need php

sudo apt-get install php5
sudo apt-get install php-mysql
sudo apt-get install phpmyadmin

---

