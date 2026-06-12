---
title: "ubuntu server help....noob"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by gascan on 2007-04-14
i am a complete noob to ubuntu linux server....i downloaded the iso, burned the cd and installed.....after rebooting i see nothing on my screen except terminal....no gui to speak of....nothing but text.....what is going on and what do i need to do....i am able to log into the box and after that i dont know what to do....any help would be greatly appreciated and thank you in advance..

gascan

---

### Post by rmemm on 2007-04-14
Yes -- that is correct.  Ubuntu server does not come with a GUI -- you can install one -- but if you do -- you'll increase size a lot and have a desktop basically.  The idea of the server (at least I think it is) is to have a very small system than can host things like web pages, nfs, databases, etc.

You'll need to use the command line to do much with the server.  Until 1983 or so all computing was done this way.  You may not like it -- but a big advantage of command line is you tell the system what you want it to do rather than doing it by a lot of clocking and dragging.  So for search and describe types of things it's actually much better than gui stuff.  Both gui and command line interfaces have their advantages.  One reason I like linux is it has both.

So what do you want to do?

Some handy commands: 

*  show directory: ls
*  change directory:  cd dirname (for example ls /home shows the users in home)
*  log out: exit
*  edit a file with nano:  nano myfile.txt
*  find out about a command, for ls:  man ls   (hint exit man with q)

Rob

---

### Post by kvonb on 2007-04-14
The only difference between the server version, and the standard desktop version is that the server ver has no GUI.

You can do exactly the same with both versions, ie if you want a web server / email server / FTP site or whatever, you can do it with both.

On my server I run the standard desktop version as I like to have GUI access, some people don't need that or they need a smaller install, so that is what the server version is.

You can "upgrade" to the GUI by typing:

```
sudo apt-get install ubuntu-desktop
```

But it will take a while, and will have to download lots of stuff.

It might be easier to download the desktop version, then if you have to re-install or want to put it on another system later you won't have to do all the downloading again.

---

### Post by az on 2007-04-14
> **gascan said:**
> i am a complete noob to ubuntu linux server....i downloaded the iso, burned the cd and installed.....after rebooting i see nothing on my screen except terminal....no gui to speak of....nothing but text.....what is going on and what do i need to do....i am able to log into the box and after that i dont know what to do....any help would be greatly appreciated and thank you in advance..

gascan

[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

Also, installing the ubuntu-desktop won't be that helpful since you can't configure any of the LAMP stack from the desktop - you will still need to use the command line.  A production server is not connected to a monitor most of the time and you usually run it remotely, from the command line.

If you do want to install the desktop, install the linux-generic package along with the ubuntu-desktop package.  Sometimes, the server kernel does not work with some desktop hardware.

---

