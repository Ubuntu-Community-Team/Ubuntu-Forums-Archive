---
title: "Installing Xubuntu 6.04.1 Server on PPC 400Mhz iMac"
date: 2008-05-22
forum: Apple Hardware Users
---

### Post by shgadwa on 2008-05-22
I am trying to install a server on this G3 PPC imac, 40Mhz.
As others said, I am supposed to do apt-get update then apt-get upgrade. Then apt-get install xorg icewm -theme menu synaptic

I tried that and it says something like that it could not find xorg or something like that......???


How do I get a server to work??

---

### Post by kerry_s on 2008-05-22
so i assume you have the base installed already?
you must have internet!

sudo apt-get update
sudo apt-get install x-window-system-core icewm menu
sudo update-menus
startx

why such a old release?

i would recommend debian build up->
net installer:
[http://cdimage.debian.org/cdimage/lenny_di_beta1/powerpc/iso-cd/debian-testing-powerpc-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_beta1/powerpc/iso-cd/debian-testing-powerpc-businesscard.iso)

just install the base like you did with ubuntu
log in as root
apt-get install xorg slim icewm menu
press> ctrl+alt+delete 
to reboot
log in and continue building.

with debian you'll be more up to date, rolling release so you only have to install the 1 time and your good to go, just update from time to time with->
apt-get update
apt-get dist-upgrade

---

### Post by shgadwa on 2008-05-22
Well, I tried 7.10 and 8.04 Dozens of times. Tried this...tried that. Fixed the date, edited the xorg file whatever...did htis did that, tried thsi tried that. IT DOES NOT WORK WITH THESE IMACS.

---

### Post by shgadwa on 2008-05-22
I did what you said to do....it says it cannot find package icewm. it has internet....??

---

### Post by shgadwa on 2008-05-22
Please let me know how I can get this working.....I could do a regular install but I hear a server isntall makes for a faster computer.

---

### Post by kerry_s on 2008-05-22
> **shgadwa said:**
> I did what you said to do....it says it cannot find package icewm. it has internet....??

when you ran> sudo apt-get update
did it update?

did the rest of the stuff install?

if so you might need to turn on some repo's, such a old version i hope there still there. :confused:

sudo nano /etc/apt/sources.list

remove any # in front of lines starting with deb

you can also try a different wm, fluxbox for instance->
(i'm going to do the whole line, just in case)
sudo apt-get install x-window-system-core fluxbox menu
sudo update-menus
startx

---

### Post by shgadwa on 2008-05-22
did the rest of the stuff install?


Yes, it did jsut fine I also tried to install server twice. I jsut did a normal isntall and it worked fine.

---

### Post by kerry_s on 2008-05-22
> **shgadwa said:**
> did the rest of the stuff install?


Yes, it did jsut fine I also tried to install server twice. I jsut did a normal isntall and it worked fine.

strange, are you double checking your spelling? i notice you have a fat finger habit like me. :)

---

### Post by shgadwa on 2008-05-30
> **kerry_s said:**
> strange, are you double checking your spelling? i notice you have a fat finger habit like me. :)

Yes, it is the correct spelling. Oh well.

I do admit to my fat finger habit.

Does anyone else know the problem here?

---

### Post by Bluehazed on 2008-05-31
How much ram do you have? If you have over 128mb, just regular install. I have an iMac G3 with a 266Mhz proccesor and 160mb of ram, and it runs perfectly, nothing ever crashes, and everthing loads fast.

I suggest you get the 6.10 alternate install. It works for me.
[http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/xubuntu-6.10-alternate-powerpc.iso](http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/xubuntu-6.10-alternate-powerpc.iso)

---

