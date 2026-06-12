---
title: "Gnome"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by lupgop on 2007-05-28
i just installed Ubuntu 7.04 server, is in meant to have a GUI ??? or pure textual input ??? can i install one ?? otherwise does any one recall how to slow down the scrolling on dir --help <GO> as i cant recall the attributes and is flies past too quick!!!

---

### Post by tkjacobsen on 2007-05-28
you can use 
```
dir --help | more
```
to view the output of dir in a more user friendly fashion. In general you can pipe the output of all commands to more for simpler output.

You can install the gnome-desktop using
```
sudo apt-get install ubuntu-desktop
```

Or you could just install a more minimal dekstop like fluxbox
```
sudo apt-get install fluxbox
```

---

### Post by lupgop on 2007-05-28
says;

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ubuntu-desktop

??

---

### Post by meborc on 2007-05-28
you should do ```
sudo nano /etc/apt/sources.list
```
then comment out (put ## infront) of the first lines with cd in them

then delete the ## from the lines starting with deb

then ctrl+o to save and ctrl+x to get back to cli

then ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```
you can use kubuntu-desktop instead of ubuntu-desktop if you like KDE or xubuntu-desktop if you like xfce (like me)

good luck :)

---

### Post by tkjacobsen on 2007-05-28
Be sure to have lines similar to the following in /etc/apt/sources.list

```

deb http://dk.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse

```
You could very well have another country-prefix than dk. (Or you can do without like [http://archive.ubuntu.com](http://archive.ubuntu.com))

then
```
sudo apt-get update
```

And try again

---

### Post by lupgop on 2007-05-28
gottit - looks like this would work except i dont think this machine is connecting to the internet , was hope the graphical interface would make it easier to work out how/why ....

---

### Post by meborc on 2007-05-28
what is your internet setup? you just plug your cable in and get dynamic IP? you hace a dhcp router? adsl with login and password?

those things are easy to set up from the command line

but first - what does "ifconfig" give you?

---

### Post by lupgop on 2007-05-28
runs through a DHCP router , was working with XP installed - just installed ubuntu... was set static on port 192.168.5.2 
ifconfig says 
lo         Link encap@Local Loopback
           inet addr:127.0.0.1 Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING MTU:16436 Metric:1
           RX packets:1248 errors:0 dropped:0 overruns:0 frame:0
           TX packets:1248 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:82912 (80.9 KiB) TX bytes:82912 (80.9 KiB)

for interest when i was installing it did say something about not seeing a network card ???

---

### Post by meborc on 2007-05-28
the ifconfig should have seen a eth0 (or similar) device... it seems your network card needs drivers... what is the make and model of wour network card? try searching this forum or wiki.ubuntu.com for your network card... sorry, i'm not good at network card drivers :)

---

