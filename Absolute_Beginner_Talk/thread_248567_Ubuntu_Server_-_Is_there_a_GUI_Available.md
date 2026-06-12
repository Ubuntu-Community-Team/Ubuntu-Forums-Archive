---
title: "Ubuntu Server - Is there a GUI Available?"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by McKenna on 2006-09-01
I have just installed Ubuntu LAMP Server and I'm wondering if there is a GUI I can install or anything just to make things a little less daunting? I am completely new to Linux and don't know even the basic commands for the command line :P

What I basically want to be able to do is use a GUI to browse the web for reading tutorials etc and then have access to the command line so I can test things out a bit.

---

### Post by MrHorus on 2006-09-01
> **McKenna said:**
> 
What I basically want to be able to do is use a GUI to browse the web for reading tutorials etc and then have access to the command line so I can test things out a bit.

So why bother installing the server edition when you can do this with the standard edition?

The point of a server installation is that everything that hogs resources (like a GUI) is stripped out so as to maximise performance.

---

### Post by bluenova on 2006-09-01
Hi McKenna,

Sorry about MrHorus's rude welcome to the forums. You can install the GUI by running:

sudo aptitude install gnome-desktop

---

### Post by justin whitaker on 2006-09-01
> **McKenna said:**
> I have just installed Ubuntu LAMP Server and I'm wondering if there is a GUI I can install or anything just to make things a little less daunting? I am completely new to Linux and don't know even the basic commands for the command line :P

What I basically want to be able to do is use a GUI to browse the web for reading tutorials etc and then have access to the command line so I can test things out a bit.

You can do the following:

1. Set up your networking...
2. apt-get update
3. Follow either the ubuntu-lite how-to 

[http://ubuntuforums.org/showthread.php?t=98233&highlight=fluxbox](http://ubuntuforums.org/showthread.php?t=98233&highlight=fluxbox)

or 

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

to set up Xorg, then either 

[https://help.ubuntu.com/community/Fluxbox?highlight=%28fluxbox%29](https://help.ubuntu.com/community/Fluxbox?highlight=%28fluxbox%29)

for fluxbox, or

[http://ubuntuforums.org/showthread.php?t=192106&highlight=openbox](http://ubuntuforums.org/showthread.php?t=192106&highlight=openbox)

for openbox. 

Have fun!

---

### Post by FuriousLettuce on 2006-09-01
You want to do

```
sudo aptitude install ubuntu-desktop
```

bluenova got it almost right :)

If you wanted a server and you're new to linux, or like using the GUI, then install the normal version. You can still install Apache, PHP, MySQL, SMTP servers etc, but you will have the graphical install as well. 

Alternatively, do as I have mentioned above; this will install the GUI on top of your current installation.

If you have any problems, just give us a shout.

---

### Post by bluenova on 2006-09-01
Ah yes, ubuntu-desktop. Thanks for the correction FuriousLettuce.

---

### Post by McKenna on 2006-09-01
Thanks for the replies guys. I was looking to set up a server so I just assumed installing the server version was the right thing to do :P Like I said, I'm totally new to this.

I have run the command above and the GUI install seems to be working away. If I have any problems I'll be sure to let you guys know.

---

### Post by justin whitaker on 2006-09-01
> **McKenna said:**
> Thanks for the replies guys. I was looking to set up a server so I just assumed installing the server version was the right thing to do :P Like I said, I'm totally new to this.

I have run the command above and the GUI install seems to be working away. If I have any problems I'll be sure to let you guys know.

Server installs allow you to pick and choose what you want to install, instead of taking the defaults from U/Kbuntu, so its just a more flexible way of using the system. For people that don't want "bloat" or are "Gentoo-ricahs" ;) this gives you control of what's on your rig.

There is no wrong way to Ubuntu. :smile:

---

### Post by FuriousLettuce on 2006-09-01
> **justin whitaker said:**
> There is no wrong way to Ubuntu. :smile:

I like that phrase

---

### Post by xpod on 2006-09-01
> We look to Scotland for all our ideas of civilisation - Voltaire

HERE HERE.............How i envy you....I too come from edinburgh BUT am stuck down here.....TAKE ME HOME SCOTLND....ALL IS FORGIVEN

Anyway sorry for butting in.........JUST had to release some of this tension

---

### Post by JMitchell on 2006-09-01
Interesting reading - what version of Ubuntu would you suggest I install for a server to host [Bugzilla]("http://www.bugzilla.org"), [RT Request Tracker]("http://bestpractical.com/rt") and [Media Wiki]("http://www.mediawiki.org")? I'll need to download the installation files etc so the ability to use firefox (or an alternative browser obviously) would be useful but after I've downloaded everything I won't necessarily need to run a UI.

I'm by no means a Linux expert, having used Fedora Core 3 a little for around a year now. However, I've pretty much got the basics now and am getting towards being comfortable with the command line only...

---

### Post by FuriousLettuce on 2006-09-01
The server edition should be fine, if you are confident in the use of lynx (a terminal-only text browser), which will allow you to download all of the installation files. Seems simpler than installing a GUI simply for firefox.

Simply do: 

```
sudo apt-get install lynx
```

and use lynx from the terminal to start it :D

---

