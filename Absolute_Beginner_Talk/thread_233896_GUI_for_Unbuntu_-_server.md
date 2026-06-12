---
title: "GUI for Unbuntu - server?"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by altamash on 2006-08-10
I am new to linux and read lot of good stuff about unbuntu. I am a lil bit familiar with Debian and how the installation work. 

With unbuntu server I dont know how to get to the xwindows interface. Do I need to install it manually or is there a command for this? Thanks

---

### Post by crackseller on 2006-08-10
for gnome:
```
sudo apt-get install ubuntu-desktop
```
for kde
```
sudo apt-get install kubuntu-desktop
```
for xfce (probably the best choice because of less resource usage, if you computer is really supposed to work as a server
```
sudo apt-get install xubuntu-desktop
```

That should do the job. I'm not sure if you have to install gdm manually, I don't think you do though.

---

### Post by Jagot on 2006-08-10
Though you may want to use aptitude instead of apt-get.  Read this to see why:

[http://psychocats.net/ubuntu/aptitude.php](http://psychocats.net/ubuntu/aptitude.php)

---

### Post by powder on 2006-08-10
Thanks for the tip, Jagot.  I never knew aptitude had this functionality! :cool:

---

### Post by tandre75 on 2006-08-11
I tried to use aptitude to install xubuntu-desktop and gdm, but now I get the following message in a blue screen:

[I]Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Weould you to view the X server output to diagnose the problem?
<Yes>  <No>[/I]


Before I can answer yes, the command-line login shows up.  How should I solve this?

---

### Post by kinematic on 2006-08-11
you have to install the x-server....sudo aptitude install xserver-xorg.

---

### Post by az on 2006-08-11
> **kinematic said:**
> you have to install the x-server....sudo aptitude install xserver-xorg.

If ubuntu-desktop is installed, so are the xserver packages.

Your graphics card is either misconfigured, or you need the desktop kernel.  

sudo apt-get install linux-386 

That will install a kernel that better handles desktop hardware - I can't rule that out as what can be causing you trouble.  After that kernel is installed, try booting into recovery mode and running

dpkg-reconfigure -phigh xserver-xorg


and then 
init 2

to get back into the desktop.

---

### Post by kinematic on 2006-08-12
> **azz said:**
> If ubuntu-desktop is installed, so are the xserver packages.

i realized that later on.
i was thinking of the install i did.
server install and added kde-core and just the things i want.....that doesn't install the x-server.....my mistake.

---

