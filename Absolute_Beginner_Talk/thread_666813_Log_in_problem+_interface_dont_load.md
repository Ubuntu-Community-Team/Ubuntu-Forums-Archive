---
title: "Log in problem+ interface dont load"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by joblo on 2008-01-13
So... this morning, I installed ubuntu (studio but that is same than normal). Install was successfull.
Sadly, When I booted, it make me hardware detection and other, then, appear the place who say me to place log in and password... I typed the login, but the password isnt writting when I want... all keys works except letters and numbers... but it make this only with the pass. After some try, it apparently logged me but no interface... just a command prompt (like nameofmypc with other symbols)... and I'm staying there... nothing more is happening...

I really need to solve that and can use my ubuntu normaly because I need it... for 2 urgent work... really important work... :mad: :( :confused:

---

### Post by sumguy231 on 2008-01-13
> I typed the login, but the password isnt writting when I want... all keys works except letters and numbers... but it make this only with the pass.
It's not supposed to show any letters or numbers while you're typing, just type it like your normally would.

On to the graphics problem:
Try running this:
```
sudo /etc/init.d/gdm start
```
And post any error output you get. Also post information about the hardware you're using, including the graphics hardware.

Edit: Oh, and read this for more info (it's from one of the stickies at the top of this forum)
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

---

### Post by joblo on 2008-01-13
It say to me invalid command :(

GC: Nvidia Geforce 7600 GS
Asus mother board dont remember what model
I runned another version of linux lomg time ago but didnt had any problems... Just because now i got a MBR virus so need to use another os

Edit: I tried the specified command on the site you linked(sudo dpkg-reconfigure xserver-xorg) but it say to me that the package isnt installed...

---

### Post by sumguy231 on 2008-01-13
It sounds like you don't even have the desktop installed for some reason - maybe you accidentally did a server install? Anywho, this should install the full desktop for you:
```
sudo aptitude install ubuntu-desktop
```
Wait a while for it to download and install all the software (it helps if you have a fast connection), and reboot when it's done by running:
```
sudo reboot
```
When it comes back up, everything *should* work fine.

---

