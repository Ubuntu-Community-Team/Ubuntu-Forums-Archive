---
title: "upgrading from dapper to server edition"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by superbeef on 2006-11-17
I have Ubuntu Dapper Drake running right now, but I want to try running a server. I heard you had to install the server version to run a server, is it possible to upgrade from regular ubuntu to server ubuntu? Or do I have to completely reinstall? I hope I don't, because I don't want to lose everything I have on it. If nothing else, can I partition my hd to have both ubuntu and ubuntu server edition? That might not work out too well either, cuz my comp only has a 20 gig hd.

---

### Post by justin whitaker on 2006-11-17
> **superbeef said:**
> I have Ubuntu Dapper Drake running right now, but I want to try running a server. I heard you had to install the server version to run a server, is it possible to upgrade from regular ubuntu to server ubuntu? Or do I have to completely reinstall? I hope I don't, because I don't want to lose everything I have on it. If nothing else, can I partition my hd to have both ubuntu and ubuntu server edition? That might not work out too well either, cuz my comp only has a 20 gig hd.

You do not need to install a server to run a server: just install the server apps. 

Ubuntu Server=core ubuntu + server applications - GNOME/KDE gui.

---

### Post by localuser on 2006-11-17
> **superbeef said:**
> I heard you had to install the server version to run a server

All you need to do, basically, is install LAMP on your normal desktop application, then remove the graphical interface (desktop).

Well, let me rephrase that, all you need to do is install AMP, since the L in LAMP stands for Linux, and you already have that installed.

So, install and configure A (Apache), M (mySQL), and P (PHP will do for this one).

If you're new to Unix/Linux, I recommend that if you want to play with the AMP thingies, don't uninstall the desktop.  You can have a "server " with a desktop, just don't tell any hard core techies that you're doing that as they may throw rocks at you :mrgreen:

---

### Post by superbeef on 2006-11-17
All right, I really appreciate it you guys. If you need any help with xboxs or ds's, let me know, that's about all I know about, lol.

---

### Post by superbeef on 2006-11-17
Hey, you wouldn't know how to get apache on here, would you? It's not in the add/remove thing at all. Probably one of those apt-get deals, isn't it? As for MySql and php, guess I don't really know what I'd need to install for those.

---

### Post by Abild on 2006-11-17
> **superbeef said:**
> Hey, you wouldn't know how to get apache on here, would you? It's not in the add/remove thing at all. Probably one of those apt-get deals, isn't it? As for MySql and php, guess I don't really know what I'd need to install for those.

What are you going to use your server for? Webserver, Fileserver, Gameserver, FTPserver or something else?

If you want a webserver you should install Apache.
To install programs which are not present in the add/remove programs feature you will have either install it via Synaptic or via the command line.

Synaptic is the graphical package manager included in Ubuntu. It can be accessed from the menus System > Administration > Synaptic

If you want to use the command line this command should do the trick:
sudo apt-get install apache2

Apache alone can only be used for serving static HTML pages. If you want to make more advanced webpages you will ned a server-side programming language(like php) and most likely also a database (like mySQL).

Apache can be started, stopped, restarted and reloaded using the following command:
sudo /etc/init.d/apache2 start
Instead of start you can insert stop, restart(restarts whole server, will take the server offline for a short while), reload(reloads configuration without taking the server offline)
It will also automatically be started at boot.

The configuration files for Apache are present in /etc/apache2. You might want to read the official apache documentation on the config file. It's pretty good. You are probably mostly interested in apache2.conf and the files present in the sites-enabled directory.

The directory for putting files that should be hosted defaults to /var/www but that can be changed in the configuration file.

If editing raw configuration files scares you off you can install something like webmin. It will provide an easy to use web interface for administrating almost every server available for Linux(including apache). It can be installed from synaptic or command line in the same way as apache2. You can access it by entering [http://127.0.0.1:10000](http://127.0.0.1:10000) in a webbrowser for accessing it from your local computer.

---

### Post by superbeef on 2006-11-17
Wow, that was extremely helpful. Is there another one of those fun little command line things to get webmin? Basically, I just want to be able to host some files off this comp so other comps can see it, so do I need to set up a domain name, or can I just use my IP? That'd be cool if I could, cuz then I'd just get a url forwarder. Thanks a lot, man.

---

### Post by superbeef on 2006-11-18
Hey, I got webmin installed, found a deb installer at their site. Anyone know how to make it so anyone can access my webserver? Whenever anyone tries to connect to it, it asks them for a user name and password, and I want it so anyone can access it.

---

### Post by superbeef on 2006-11-25
Hey, I figured out how to do this, so I'll post just in case anyone else is wondering. Basically, from then on you change your router's settings to forward port 80 to the local IP of the computer running the server. Not too bad. Thanks again to you guys who helped me out.

---

