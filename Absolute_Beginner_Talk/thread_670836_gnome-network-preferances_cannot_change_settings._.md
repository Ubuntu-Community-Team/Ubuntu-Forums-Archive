---
title: "gnome-network-preferances cannot change settings.  enviornment variables?"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by mooglinux on 2008-01-17
I installed dansguardian with tiny proxy a little while ago and have since removed them. Now i cannot connect to download from the repositiries whether it be through synaptic, add/remove programs, or apt-get. After a lot of poking around and reading up on things, i have learned that my http_proxy enviornment variable is goofy, and needs to be changed back or removed. however, i am stumped how to do this. gnome-network-preferances gives me this error when i open it:
```
The application "gnome-network-preferences" attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change. Some of the settings you have selected may not take effect, or may not be restored next time you use the application.
```
clicking 'details' tells me this:
[COD Can't overwrite existing read-only value: Value for `/system/proxy/mode' set in a read-only source at the front of your configuration path[/CODE]

/etc/enviornment
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US.UTF-8"
```

sample error message when trying to fetch the repo indexes:
```
http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg: Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
```

so the http_proxy variable is set to connect to localhost at port 8080 but i cannot figure out how to fix this. i need to be able to use gnome-network-preferances as we will be setting up a proxy server soon and i need an easy way to connect to it, without setting enviornment variables if possible (at least using a gui anyways)

---

### Post by smurphy_it on 2008-01-18
Apparently using Tiny Proxy started your problem.  There is a bug which explains some of this, plus at the bottom of the web page it explains the gconf-edit things you can do to unset it.  Try that.

[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/78098]("https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/78098")

Let me know if that helps, if not, I'll check on a linux system later.

---

### Post by mooglinux on 2008-01-18
The problem described in that bug is precisely what is going on here, but im afraid i dont see the solution on that page, or at least not clearly enough for me to understand. They talk about it on dapper and fiesty but obviously it stil exists in gutsy as well. 

So somehow or other, i want the gnome-network-preferences to modify http_proxy which right now it is not. :/

---

### Post by mooglinux on 2008-01-20
*bump* 

surely someoen has got to know how to fix this? i need to change the http_proxy or whatever enviornment variable back again to someting that works properly. the updates i need are stacking up and i also would love to be able to install programs from add/remove again!

---

### Post by mooglinux on 2008-01-21
how about just manually changing the http_proxy variable? i need an easy command i can run from the terminal, going in and editing files might be beyond me

---

