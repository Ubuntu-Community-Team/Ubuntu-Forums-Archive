---
title: "Server with GUI?"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by stuartindigo on 2007-03-15
At present the server version of ubuntu is purely commandline driven. This makes it virtually impossible for someone who is unfamiliar with linux to use.

For example - I wish to set up a testbed server running ubuntu, but installing the server version such that it is easily manageable is almost impossible without a lot of linux knowledge (infact according to aptitude using the LAME server setup failed).

Is there an easy guide to making this possible somewhere, or how to add LAME capabilities to the version I've now installed on this machine (alternate)?

Stuart

---

### Post by taurus on 2007-03-15
If you want to install Gnome on your server, just run

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by lamalex on 2007-03-15
:lolflag: i think you mean LAMP? LAME sounds like you're making fun of it! two ways to go about it, easier is to install server and then do as the previous poster said and apt-get ubuntu-desktop. otherway is to install desktop and apt-get apache, mysql, php, and the likes.

---

### Post by PetePete on 2007-03-15
you could always install webmin

download the .deb it off the website, then use apt-get to grab the dependencies.
theres a thread on these forums somewhere that has instructions.

---

### Post by az on 2007-03-15
> **stuartindigo said:**
> (infact according to aptitude using the LAME server setup failed).

Is there an easy guide to making this possible somewhere, or how to add LAME capabilities to the version I've now installed on this machine (alternate)?

Stuart

If Aptitude or any other package manager is telling you that the packages are not properly installed, it's because there is a problem.

To easily install and run the LAMP stack on any Ubuntu box, see:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Bram77 on 2007-03-15
If you want an easy manageable but powerfull Linux server you could try ClarkConnect. You can manage it thrue a integrated webinterface that is real easy to understand and it is fully customisable. I've been using it for three years now. Rock solid and no Linux knowledge is needed to install it or manage it. It's based on RedHat and uses apt, so it feels simular to Ubuntu if you would like to do things thrue a terminal session.


[www.clarkconnect.com](www.clarkconnect.com)

It's perfect for
Samba filesharing
Webserver
Database server
Mailserver
Proxyserver
Gateway (pretty advanced)
and so on...these are installable by default

Stuf I've had running perfectly on it..
nTop (network usage monitoring and client information)
Asterisk
Webmin
Usermin
and so on...

---

### Post by stuartindigo on 2007-03-15
> **taurus said:**
> If you want to install Gnome on your server, just run

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

Gives sudo: /etc/init.d/gdm: command not found

gdm is not in init.d

Aaaarrrrgggggghhhhhh!

Stuart

---

### Post by annda on 2007-03-15
try installing gdm package separately:

sudo aptitude install gdm

---

### Post by zvacet on 2007-03-15
> Gives sudo: /etc/init.d/gdm: command not found
ofcourse not because you give the wrong command. Right one is 
```
sudo /etc/init.d/gdm start
```

---

### Post by stuartindigo on 2007-03-15
I'd given it the command correctly - it just hadn't installed the gnome properly the first time by the look of things - and it appears to be having serious problems with the fonts this time...

(beginning to think about fedora)

Stuart

---

### Post by stuartindigo on 2007-03-16
Sort of getting there - but hideously slow doing anything now - taking an hour or so to boot up!

Eventually opens up file browser window, which when closed leaves a completely empty desktop (ie background only - no launcher bars) - any ideas anyone?

Stuart

---

### Post by scxtt on 2007-03-16
just a thought ...

if you want a GUI (or NEED a GUI) - don't install the server disto - install a non-server distro ...

installing the server distro then complaining you can't get the GUI going isn't very useful IMO ...

install a GUI-based distro and add your server/LAMP elements if you're not comfortable going CLI-only ...

---

### Post by Rams_god on 2007-03-16
Please run the following commands to get the GUI: I tried it and these commands works fine for me:

sudo apt-get update
sudo apt-get install xorg*
sudo apt-get install gdm
sudo apt-get install ubuntu-desktop

and then run sudo /etc/init.d/gdm start

If you are still facing an issue in bringing up the GUI then run sudo apt-get install gnome* and again run /etc/init.d/gdm start

I hope it will work.

Thanks,
 Rams.

---

### Post by az on 2007-03-16
> **stuartindigo said:**
> Sort of getting there - but hideously slow doing anything now - taking an hour or so to boot up!

Eventually opens up file browser window, which when closed leaves a completely empty desktop (ie background only - no launcher bars) - any ideas anyone?

Stuart

I would run this to fix any broken (not well installed) packages:

sudo apt-get -f install

> **scxtt said:**
> just a thought ...

if you want a GUI (or NEED a GUI) - don't install the server disto - install a non-server distro ...

installing the server distro then complaining you can't get the GUI going isn't very intelligent IMO ...

Not to mention that the server kernel does not handle some desktop-type hardware thinggies very well, including some types of mice, for example.

To switch from the server kernel to the desktop one, run

sudo apt-get install linux-generic linux-image-server*-

(or for Dapper)

sudo apt-get install linux-386 linux-image-server*-

---

### Post by stuartindigo on 2007-03-16
> **scxtt said:**
> just a thought ...

if you want a GUI (or NEED a GUI) - don't install the server disto - install a non-server distro ...

installing the server distro then complaining you can't get the GUI going isn't very intelligent IMO ...

install a GUI-based distro and add your server/LAMP elements if you're not comfortable going CLI-only ...

If you look at the rest of the thread - that was the advice earlier................

This is meant to be the absolute beginners forum. The tone of some of the responses has been less than helpful, in some cases downright rude!

something has worked - tried Rams_god suggestions and nothing updated, but I now seem to have a sensible desktop.

Now to see if I can get the system working so that I can use it for a mysql/php testbed for a project I'm working on. (and as a desktop system that I can let visitors use without them destroying my xp dev machine)...

Stuart

---

### Post by Luk0r on 2007-03-16
```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```
should do the trick.  Do this as soon as you finish the server installation, any errors you get won't cause problems.

The reason the GUI isn't included with the server installation is because... it's a server OS install.  As you become more familiar with Linux and play around with the console a bit, you'll be able to confidently remove the GUI and administrate things yourself from the command line.  It only takes time and patience, that's all.

---

### Post by stuartindigo on 2007-03-16
Yet more problems - can't set any file permissions$"!%

Set up a user using the graphical pureftp i/f and can't ftp in (permission denied despite being legal)-so now have a system that I can't do anything with.

Can't even create a folder to act as a share within the www root (so can't copy the site I want to test over).

I'm now having to try fedora out of sheer frustration.

Stuart

---

