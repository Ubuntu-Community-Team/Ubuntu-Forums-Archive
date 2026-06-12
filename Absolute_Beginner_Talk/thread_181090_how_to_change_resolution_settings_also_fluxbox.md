---
title: "how to change resolution settings? also fluxbox?"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by str8flexx on 2006-05-23
how would i go about this? i just installed the ubuntu (server) and when i boot up my system it takes me to a command prompt asking me to sign in. i want to also no how to install fluxbox. 

thanx in advance

---

### Post by Kelvin on 2006-05-23
Heya str8flexx,

I'll leave the resolution question till the last, it's probably more easily dealt with after you have x and fluxbox in place.

This is off the top of my head, and I don't know what your system is, Breezy or Dapper, if you have a graphics card, etc., but here's a rather generic path to getting the latest fluxbox up and running on top of a server install. I've heard complaints about the fluxbox in the repositories.

Forgive me if this is too basic, just covering all the bases.

+++  

First of all, do sign in, then, at the prompt


1: Open your sources list.

```
sudo nano /etc/apt/sources.list
```
 
2: Enable universe repos. Delete the # character from in front of the universe lines, then hit ctrl-x, and y to save and exit.

3: Update

```
sudo apt-get update
```
 
4: Install a few base packages

```
sudo apt-get install x-window-system-core xserver-common xfonts-base gdm
```

5: Download the most recent .deb file from Dopey's blog.  

```
wget http://logicvortex.net/tmp/fluxbox/sarge/fluxbox_0.9.15.1-1_i386.deb
```

6: Install the file.

```
sudo dpkg-i fluxbox_0.9.15.1-1_i386.deb
```

7: Set up the fluxbox/startup file

```
nano ~/.fluxbox/startup
```

… and put this in there 

```
exec /usr/local/bin/fluxbox -log ~/.fluxbox/log
```

8: Make an entry for fluxbox in GDM, type… 

```
cd /usr/share/xsessions
nano fluxbox.desktop
```

…and put this in there :

```
[Desktop Entry]
Encoding=UTF-8
Name=Fluxbox
Comment=This is fluxbox
Exec=/home/(username)/.fluxbox/startup
```

9: Logout, then log back in to Fluxbox. You /should/ now have a session entry for fluxbox in your graphic log-in screen... If you have a graphics card, you will need to install the driver for it and then reconfigure a few things to make it all happy, including the screen resolution. If that happens, post back.

Good luck. I hope this helps.

---

