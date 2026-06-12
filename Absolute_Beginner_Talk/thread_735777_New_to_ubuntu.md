---
title: "New to ubuntu"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by neojam on 2008-03-26
Hi All,

I could use some help. My friend and i are working on an idea for remote music recording and after surfing   the web we saw that unix/linux is the best way to go to try and work out this idea. The problem is that we are both windows base IT techs and are very new to the Linux world. The place that we work for has been kind enough to let us have 2 of their older servers that they no longer need and we would like to install ubuntu 7.10 server software on them.

 I have just installed it 7.10 server on my 2nd hard drive on my home PC to see what it looks like and to get a feel of it. What i notice was that when it loads up it goes to a command promt screen instead of a graphic user interface like windows servers. One of questions would be is this normal and is there a graphic user interface for ubuntu server? I have looked on the unbuntu site for a user manual or links that discribe this server product but so far i have not been able to find any thing.

Any advice and/or helpful links on starting and using the ubuntu 7.10 server will be a great help. We are both really excited about learning this and becoming apart of this community.

Thank you

Neojam

---

### Post by iSplicer on 2008-03-26
The servers only offer a command line interface, no GUI. You should have installed the desktop version =)

Dont worry, just type this into your command line while you are in ubuntu server:

```
sudo apt-get install ubuntu-desktop
```

you may also want to consider xubuntu if the computer is very old

Good luck!

---

### Post by zen_waters on 2008-03-26
Hi,

Ubuntu desktop may be a good starting point if you need a GUI... remember many of the same packages WEB, SQL, etc will be available on both versions.  

The server version is tuned more for people installing to production servers.

Jeremy

---

### Post by jan quark on 2008-03-26
the posters above are right

the server edition do not come with a gui

the desktop edtion ( live cd for graphical installation and alternate CD for text-based installation) does.

have a look at aysiu's site as a starting point for your linux journey and feel free to ask
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by kostkon on 2008-03-26
> **neojam said:**
> Hi All,

I could use some help. My friend and i are working on an idea for remote music recording and after surfing   the web we saw that unix/linux is the best way to go to try and work out this idea. The problem is that we are both windows base IT techs and are very new to the Linux world. The place that we work for has been kind enough to let us have 2 of their older servers that they no longer need and we would like to install ubuntu 7.10 server software on them.

 I have just installed it 7.10 server on my 2nd hard drive on my home PC to see what it looks like and to get a feel of it. What i notice was that when it loads up it goes to a command promt screen instead of a graphic user interface like windows servers. One of questions would be is this normal and is there a graphic user interface for ubuntu server? I have looked on the unbuntu site for a user manual or links that discribe this server product but so far i have not been able to find any thing.

Any advice and/or helpful links on starting and using the ubuntu 7.10 server will be a great help. We are both really excited about learning this and becoming apart of this community.

Thank you

Neojam

Yes, the Ubuntu server comes with no desktop environment. If you like, you can install a lightweight one afterwards. You'll not want to install the full Ubuntu desktop, since it is supposed to be a server. You could install the Xubuntu desktop, which is more light, by doing
```
sudo apt-get install xubuntu-desktop
```

---

### Post by djbsteart1 on 2008-03-26
Before you install a GUI on the server, make sure you look at what each one is about. There is piles od docs available in the wiki. The ones to look for are xubuntu which uses XFCE for its GUI, ubuntu which uses gnome, and kubuntu which uses KDE. Xubuntu is the lightest, with KDE and gnome being debatable. 
As no one has giving the code for kubuntu, 
```
sudo apt-get install kubuntu-desktop
```

For more info, I found this site useful: [here]("http://www.psychocats.net/ubuntu/kde")

---

