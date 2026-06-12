---
title: "Ubuntu 6.06 install q's"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by chris96 on 2008-03-27
Hello, this is my first post to this forum.

I have installed 6.06 server edition on a clean hd and everything seemed to go alright. When I boot the pc, it comes up with a command prompt/login. 

The documentation for the 6.06 describes a desktop environment, "The default desktop environment for Ubuntu is GNOME, a leading UNIX and Linux desktop suite and development platform." 

Should this server boot directly to GNOME? If not, how do I start GNOME from the command interface?

I have searched the documentation and the forum with no luck.
thanks,
chris

---

### Post by BillDozer on 2008-03-27
Hi,

If you, like you said, installed the server edition, it does not start up with a desktop environment.

If you like to have a desktop environment, you could write:```
sudo apt-get install ubuntu-desktop
```
This will install the default Gnome desktop, if you really want to use the PC as a server, you rathere would install a different flavour windows manager. xubuntu-desktop uses xfce with is a much more lightweight window manager.

---

### Post by chris96 on 2008-03-27
Thanks BillDozer. I am new to Linux and haven't used a Unix type OS since school back in early 90's. I am setting up this pc to be a web server (lamp). I am not too worried about performance right now... my connection speed is only 512k. Mostly I want to learn how to setup and secure the server, then practice attacking it from the outside!
chris

---

### Post by Joeb454 on 2008-03-27
When you install the server it should ask you what you want to install.

Though I don't know about 6.06, my server is running 7.10 :)

Don't forget to update your server if you want to secure it ;) ```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by chris96 on 2008-03-27
BillDozer,
I tried your suggestion, but get an error:
E: Couldn't Find package ubutu-desktop

Is this package in that huge iso download or do I need to be connected to the internet?
thanks,
chris

---

### Post by zvacet on 2008-03-27
Type in terminal

```
sudo nano -Bw /etc/apt/sources.list
```

add this line

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse

Ctrl+o > Enter >Ctrl+x

```
sudo apt-get update && sudo apt-get upgrade
```

For GNOME

```
sudo apt-get install ubuntu-desktop
```

for KDE

```
sudo apt-get install kubuntu-desktop
```

for Xfce

```
sudo apt-get install xubuntu-desktop
```

You choose which one you like.

---

### Post by chris96 on 2008-03-28
I tried all of the suggestions and it took overnight to download all of the upgrades/updates etc. No when I type sudo apt-get install ubuntu-desktop, it asks if I want to download another 433mb of data (which I said yes to last night and let it download again).. this time I say 'no' and it aborts. According to the readout after entering the command, all the updates / upgrades have been downloaded ok.

Any suggestions on how to get the GNOME desktop started?
thanks.

---

### Post by zvacet on 2008-03-28
```
sudo /etc/init.d/gdm start
```

or 

```
startx
```

---

