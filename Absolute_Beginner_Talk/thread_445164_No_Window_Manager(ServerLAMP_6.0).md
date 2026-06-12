---
title: "No Window Manager(Server/LAMP 6.0)"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by OzzMosiz on 2007-05-15
I've just downloaded and installed Ubunto 6.? Server and installed it with LAMP, when it boots no Window Manager launches, so I login and can't see any gnome manager.

I've done a google search and can't find any help. Also it doesn't seem to be picking up my Wireless Network, so I plugged the RJ45 directly into my PC and still won't access the network.

Am I being stupid??
edit: I think I've been a dumb-a55 and downloaded the wrong version for what I want :-D

---

### Post by benfindlay on 2007-05-15
The point of the LAMP is to run your server with the bare minimum drain on system resources. The LAMP server has no GUI, but you can install it by typing ```
sudo aptitude install ubuntu-desktop
```

Hope this helps!

---

### Post by chamberlain2006 on 2007-05-15
No, you're right, there is no gnome/window manager.  But that's what the server install is - a basic server install designed to optimize server capabilities, which does not always need a window manager.  If you do need Gnome, you may want to do a fresh install with the Desktop CD.  That will mean that you need to install LAMP again (not terribly difficult).  If you want the full desktop package, install the ubuntu-desktop package ```
sudo apt-get install ubuntu-desktop
```
Your other option is to follow [this]("http://doc.gwos.org/index.php/LightweightGnome") guide for installing lightweight Gnome.

I hope you're enjoying Ubuntu and you can resolve your problems!

---

### Post by benfindlay on 2007-05-15
Just done some looking online myself.

First however I think you need to edit your repositories. type ```
sudo nano /etc/apt/sources.list
``` and enable the multiverse and universe repos

Then type ```
sudo apt-get update
``` then you can type ```
sudo aptitude install ubuntu-desktop
```

Hope this helps!

---

### Post by OzzMosiz on 2007-05-16
Thanks guys for your help, much appreciated. Any idea why the networking doesn't work (wireless or ethernet)?

---

