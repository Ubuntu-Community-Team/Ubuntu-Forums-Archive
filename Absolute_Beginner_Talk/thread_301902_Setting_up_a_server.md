---
title: "Setting up a server"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by Bill007 on 2006-11-17
Is setting up the ubantu server best done from the command line or is there a user freindly interface that it can be done thru

Regards Bill007

---

### Post by taurus on 2006-11-17
Well, it depends what you install on your machine.  If you use the server version, then it's a command all the way unless you install a window manager like Gnome, KDE, XFce4, fluxbox, etc.  But if you install the desktop or the alternate version, then you have a nicce Gnome to play with...

Either way, it's up to you if you want to configure everything from a command line or through a terminal!

---

### Post by Bill007 on 2006-11-17
I have intalled the base ubantu 5.10 system (server)

so if I install Kubantu I can set this up as server

My problem at present is configuring the network static ip thru  command cant seem to  make the flie changes stick and cant reach webmin thru a remote networked machine

---

### Post by taurus on 2006-11-17
Yes, you can install KDE or Gnome after you have set it up as a server.  Run these at the prompt then.

```
sudo aptitude update
sudo aptitude install kubuntu-desktop <-- for KDE
sudo aptitude install ubuntu-desktop <-- for Gnome
(You don't have to install both...)
```

---

### Post by Bill007 on 2006-11-17
I will keep trying the command line as I do like the challange

One more quick question while I have  your attention how can open the synaptic package manager from the command line 

I am following i guide i got off line and it says to do this

To enable the Universe servers, I did

sudo nano /etc/apt/sources.list

Inside that file, uncomment the two lines that look something like this:

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

Hit Control O to save and press enter to use the same filename. Then press Control X to close Nano.

I could probably enable the Multiverse stuff in there too, but as I’ve not tested it like that, I’ll leave it to exactly how I did it.

Open up the Synaptic Package Manager 1. Settings 2. Repositories 3. Add 4. Check Multiverse 5. Click OK and let it rescan the servers.

You can then close Synaptic. apt is now all set up ready for installing the packages we need.

---

### Post by taurus on 2006-11-17
You can't open synaptic from a command line because you don't have X running!!!  Therefore, you can use either apt-get or aptitude to install other apps.  And if you install synaptic, it will also download and install a bunch of stuff for Gnome for you...

```
sudo apt-get update
sudo apt-get install <app name>
```

---

### Post by Bill007 on 2006-11-17
fantastic installed synaptic from the command line good buzz with this installed 

Probably a stupid question for some one of your experience but here goes

how do i get to synaptic now its installed promise I will let you go after this question I am most appreciative of your time taurus:D 

Regards Bill007

---

### Post by taurus on 2006-11-17
> **Bill007 said:**
> fantastic installed synaptic from the command line good buzz with this installed 

Probably a stupid question for some one of your experience but here goes

how do i get to synaptic now its installed

Are you still in a command line?  To run synaptic, you need to have a window manager run first so if you want something light and small, you can go with fluxbox or Xfce4...

```
sudo aptitude install xubuntu-desktop
-or-
sudo aptitude install fluxbox
```

> promise I will let you go after this question I am most appreciative of your time taurus:D 

Regards Bill007

If you have questions, just ask them away.  Will try to answer them as best as I can.

---

### Post by Bill007 on 2006-11-17
you are to kind Taurus I will get to the command line

---

### Post by az on 2006-11-17
> **Bill007 said:**
> I have intalled the base ubantu 5.10 system (server)

so if I install Kubantu I can set this up as server

My problem at present is configuring the network static ip thru  command cant seem to  make the flie changes stick and cant reach webmin thru a remote networked machine

You can install the LAMP stack on any Ubuntu box, be it command line only or a desktop system like  Kubuntu, Ubuntu or any other one.  The LAMP packages do not interfere with the desktop and vice versa.

If this is for a production server, it is better to install and use less, so just use the command line.

As for your problems, once you edit the /etc/network/interfaces file, you have to bring the connection down and then back up:  Either do

sudo ifdown eth0
and then

sudo ifup eth0

or just do

sudo /etc/init.d/networking restart

If you are running webmin, if your network interface is working, you should be seen on the network.

Why are you running breezy?

---

### Post by Bill007 on 2006-11-17
I will be using this as production server for my webdevelopment and also hope to use this server in my accommodation Business as a common place of Backup  

As far as using breezy I have no idea other then its 1 of 2 disks that i had 

I have kubantu 6.06 as well  your suggestions  would be welcome

---

### Post by az on 2006-11-18
> **Bill007 said:**
> 
I have kubantu 6.06 as well  your suggestions  would be welcome

Download the 6.06-1 server cd and install that.  Avoid the GUI since anything non-essential installed on a production box is a security risk.  Use Dapper (6.06-1) because it is a LTS version which means it it a little more stable and has better support.  It will be supported on the server for another four and a half years, too.  Breezy will no longer be supported in twelve months.

---

