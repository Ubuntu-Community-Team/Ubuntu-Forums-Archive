---
title: "Epiphany\Fire. Uninstall question"
date: 2005-11-01
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2005-11-01
I would like to uninstall firefox  but everytime I try to remove the item using synaptic it also wan't to remove 'gnome-core' along with 'epihany'.

Now, 'Gnome-core' I am pretty sure I need to run GNOME with and I would like to use 'Epiphany'. So how do I remove just firefox and not Epiphany or Gnome-Core?

---

### Post by Kyral on 2005-11-01
hmmm, can you give the output from

sudo apt-get remove firefox -s

(It will just simulate it)

---

### Post by nitricacid on 2005-11-01
nitricacid@ubuntu:~$ sudo apt-get remove firefox -s
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  epiphany-browser epiphany-extensions firefox gnome-app-install gnome-core
  mozilla-mplayer yelp
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
Remv epiphany-extensions [1.8.1-0ubuntu1]
Remv epiphany-browser [1.8.2-0ubuntu1]
Remv gnome-core [1:2.10.1.1ubuntu1]
Remv yelp [2.12.1-0ubuntu1]
Remv gnome-app-install [0+20051005]
Remv mozilla-mplayer [3.05-1ubuntu1]
Remv firefox [1.0.7-0ubuntu20]
nitricacid@ubuntu:~$

There ya are :)

---

### Post by Kyral on 2005-11-01
Well, Epiphany depends on Firefox, so I knew that would happen. So does gnome-app-install, and yelp. Gnome-core is just a metapack to pull in everything GNOME needs (Kinda like how Ubuntu-Desktop, Kubuntu-Desktop, Edubuntu-Desktop, and Xubuntu-Desktop work).

---

### Post by nitricacid on 2005-11-01
Well if i can't uninstalled and just use epiphany it's no big deal. I was just bascily asking if there was another way around synaptic removing GNOME-Core along with the other stuff.

Thanks anyway. :)

---

### Post by Brian McConnell on 2005-11-21
[QUOTE=Kyral]Well, Epiphany depends on Firefox, so I knew that would happen. So does gnome-app-install, and yelp. Gnome-core is just a metapack to pull in everything GNOME needs (Kinda like how Ubuntu-Desktop, Kubuntu-Desktop, Edubuntu-Desktop, and Xubuntu-Desktop work).[/QUOTE]
So is it okay to go ahead and remove the desired package along with gnome-core? Will your desktop environment remain intact or will it get deleted as well?
I want to remove some progs, but Synaptic states it will have to remove gnome-desktop-environment, so I got gun-shy. And I sit here thinking "isn't removing gnome-desktop-environment a bit extreme when all I really want to do is remove a web browser"?
help!

---

### Post by Kyral on 2005-11-21
gnome-desktop-environment is also just a meta-pack it seems (heck its also from Universe).

When in doubt, tag -s onto the end of the Apt-Get command to simulate it

---

### Post by Brian McConnell on 2005-11-21
[QUOTE=Kyral]gnome-desktop-environment is also just a meta-pack it seems (heck its also from Universe).

When in doubt, tag -s onto the end of the Apt-Get command to simulate it[/QUOTE]
I took that as a "yes" and am doing fine. Thanks for your helpful information.
All the Best,
Brian

---

