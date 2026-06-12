---
title: "desktop environment on linux server"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Russellvg on 2007-03-30
I have a linux server running ubuntu 6.06 and I was wondering if it's possible to put a desktop environment like KDE Desktop on it.

---

### Post by christhemonkey on 2007-03-30
Yes, just:
```
sudo apt-get install kubuntu-desktop 
```

---

### Post by taurus on 2007-03-30
Yes.

```
sudo aptitude update
sudo aptitude install kubuntu-desktop kdm
sudo /etc/init.d/kdm start
```

---

### Post by charles.g.moore on 2007-03-30
> **Russellvg said:**
> I have a linux server running ubuntu 6.06 and I was wondering if it's possible to put a desktop environment like KDE Desktop on it.

sudo aptitude update
sudo aptitude install kubuntu-desktop

It certainly is no problem as long as your server has the hardware resources to handle it

---

### Post by stokedfish on 2007-03-30
It's possible, but it doesn't make much sense.

Servers need no GUIs, waste of CPU and RAM.

---

### Post by Russellvg on 2007-03-30
How could I make it so i could choose when to load the desktop environment, I don't always want it up. Like stokedfish said, it would waste cpu and ram.

---

### Post by stokedfish on 2007-03-30
Well, what for do you need it anyway? On a server??  *puzzled*

---

### Post by Russellvg on 2007-03-30
It would be easier to move around, I'm not very good at using terminal, besides, the servers not doing anything except file storage.

---

### Post by charles.g.moore on 2007-03-30
I think what you have to do is:

edit the /etc/inittab file
look for:

]# The default runlevel.

id:2:initdefault

Change the 2 to a 3
This will set your default runlevel to the CLI

Then when you want to start the x server I think you could type startx at the CLI

---

### Post by stokedfish on 2007-03-30
> **Russellvg said:**
> It would be easier to move around, I'm not very good at using terminal, besides, the servers not doing anything except file storage.
sudo apt-get install mc  ;)

[http://www.ibiblio.org/mc/images/mc-panels.png](http://www.ibiblio.org/mc/images/mc-panels.png)

---

### Post by compmodder26 on 2007-03-30
> **charles.g.moore said:**
> I think what you have to do is:

edit the /etc/inittab file
look for:

]# The default runlevel.

id:2:initdefault

Change the 2 to a 3
This will set your default runlevel to the CLI

Then when you want to start the x server I think you could type startx at the CLI

That would work, but with one modification:

You need to remove the symbolic link for "S13gdm" from "/etc/rc3.d/"

Edit:  actually, upon inspection, I couldn't locate /etc/inittab on my machine.  If that is the case for the OP, he would need to just remove the symbolic link for "S13gdm" in "/etc/rc2.d".

---

### Post by Russellvg on 2007-03-30
is it possible for the desktop environment to load when i use ssh?

---

### Post by Wicca on 2007-03-30
> **Russellvg said:**
> It would be easier to move around, I'm not very good at using terminal, besides, the servers not doing anything except file storage.

Well, if the server is not doing anything but serving files, why do you need a GUI to move around? For serving files you need to go with Samba or NFS, and both need the terminal to setup anyway.

But I recognize your thinking. I am a M$ sysadmin and raised with GUI's. When I moved over to Ubuntu I desperately wanted a GUI on my servers cause I couldn't imagine I could live without them. But some threads here on the forum made me thinking.
I tried, dived into the deep and it all went well. I CAN live without a GUI. Sure, I had to learn some new stuff, but in the end I even find it much more fun and rewarding. I succesfully *unGUIed* myself. \\:D/

You can install a desktop as mentioned, but remember that, besides a desktop, you also get a bunch of programs like, for instance, Evolution, OpenOffice, games etc.etc. They will all sit on your HDD and some even maybe in Memory waiting for you to touch it. Which you never will.

There's a third approach as well. Administer your server over the network from another machine with a GUI on it. You can do that with Webmin: [http://www.webmin.com]("http://www.webmin.com")
In that case you will have some sort of a GUI to move around, but don't need one on your server.

---

### Post by Russellvg on 2007-03-30
I have 2 servers, one is a source dedicated server and the other one is just there for storage.  I'm not planing on giving the source server a gui and just think it would be cool if the other storage server had one.  If I install a GUI on the storage server, is it possible to use the GUI when I access the server through ssh?

---

### Post by Wicca on 2007-03-30
> **Russellvg said:**
>  is it possible to use the GUI when I access the server through ssh?

In many ways, yes.
1] You have to setup a tunnel over ssh on which you'll forward X. This can be done in a one-line command. Then you can start i.e. Firefox on the remote server. Although a GUI, you won't see the desktop of the remote server, nor the panel. You'll only see a Firefox window within your local desktop session.

2] Use VNC. Again you make a tunnel over ssh and forward VNC over it. In that case you'll see the desktop of the remote server as you were sitting right behind the remote keyboard. You have to setup a VNC server on the remote server though.

3] This ssh and tunneling is overkill and useless If both servers are on the same (home)network behind a router. You can connect with VNC directly, or, much better, use rdesktop:
Applications -> Internet -> Terminal Server Client and pick VNC as the protocol.

---

