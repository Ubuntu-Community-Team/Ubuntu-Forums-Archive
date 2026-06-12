---
title: "Need help on a pretty mest up ubuntu installation"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by fasoulas on 2007-01-13
I pretty mest up my ubuntu installation i can only access the command line  and i can't backup my data so now i have to format it.

So i saw on a lot of websites that if u are multibooting with windows and u have grub installed along with ubuntu(like me) and after when u format your ubuntu partition u won't be able to access anything, even your windows partition

Is that true ?
If yes how can i avoid it and reinstalling ubuntu without problems ?

Please if u wonna help me fix my pc post only if u are sure about what u are going to post because i am in this situation because of faulse information i got from some people here(hope u didn't misunderstood me)

So anyone who nows what to do help

---

### Post by apjone on 2007-01-13
WHen you boot to ubuntu to does it say something like

Unable to start Sorg  / Xserver

---

### Post by chaplanger on 2007-01-13
I had a similar situation occur and I reinstalled Ubuntu using the live CD.  When I booted in using the Live CD I opted to completely re-install the operating system by running its install feature and made certain that I chose the same partition Ubuntu was currently installed in and then opted to totally reformat that partition.  Of course everything formerly in that partition was lost, but the GUI was back and Grub properly booted (into either Ubuntu or Windows) after the re-installation.  This was my experience.

I would do this ONLY as a last resort.  There are others on these boards that can help you find a way to restart the GUI.

Good Luck.

---

### Post by fasoulas on 2007-01-13
[http://ubuntuforums.org/showthread.php?t=333504&highlight=remove+beryl](http://ubuntuforums.org/showthread.php?t=333504&highlight=remove+beryl)

That is the other tread i opened 5 days ago in order to fix my ubuntu and trust i tried alot of things but nothing worked .

As for what [B]apjone ... 
what i see when i turn it on is something like this [/B]myname@myname-desktop:login


and i have to put my username and password put i still be in command line

commands like:
```
sudo startx
```
don't work it says something like /.Xauthority

---

### Post by mikewhatever on 2007-01-13
Before formatting Ubuntu partition, your must fix the MBR. If you are absolutely certain you must format, see the following page for instructions:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Don't rush in, but read carefully. Use it as your last possible solution, because once formated, all data on that partition is lost.

---

### Post by fasoulas on 2007-01-13
> **chaplanger said:**
> I had a similar situation occur and I reinstalled Ubuntu using the live CD.  When I booted in using the Live CD I opted to completely re-install the operating system by running its install feature and made certain that I chose the same partition Ubuntu was currently installed in and then opted to totally reformat that partition.  Of course everything formerly in that partition was lost, but the GUI was back and Grub properly booted (into either Ubuntu or Windows) after the re-installation.  This was my experience.

I would do this ONLY as a last resort.  There are others on these boards that can help you find a way to restart the GUI.

Good Luck.

Were u multibooting with windows when u had this situation?

---

### Post by bigken on 2007-01-13
at the command promt give these a try 

sudo apt-get update

sudo apt-get upgrade

sudo aptitude install ubuntu-desktop

also give this 1 a shot 

sudo dpkg-reconfigure xserver-xorg 

good luck ;)

---

### Post by fasoulas on 2007-01-13
> **mikewhatever said:**
> Before formatting Ubuntu partition, your must fix the MBR. If you are absolutely certain you must format, see the following page for instructions:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Don't rush in, but read carefully. Use it as your last possible solution, because once formated, all data on that partition is lost.

Thnx alot for the information and the link but i want your opinion on this link

[http://www.mainframe.gr/index.php/2006/08/28/how-to-get-rid-of-linux/](http://www.mainframe.gr/index.php/2006/08/28/how-to-get-rid-of-linux/)

---

### Post by fasoulas on 2007-01-13
> **bigken said:**
> at the command promt give these a try 

sudo apt-get update

sudo apt-get upgrade

sudo aptitude install ubuntu-desktop

also give this 1 a shot 

sudo dpkg-reconfigure xserver-xorg 

good luck ;)

Thnx i will make a last try

---

### Post by fasoulas on 2007-01-13
> **bigken said:**
> at the command promt give these a try 

sudo apt-get update

sudo apt-get upgrade

sudo aptitude install ubuntu-desktop

also give this 1 a shot 

sudo dpkg-reconfigure xserver-xorg 

good luck ;)

Tnx a lot man u just save my day i thing the only thing i had to do was

```
 sudo aptitude install ubuntu-desktop
```

because the other commands i tried them before

THnx a lot again 

i have 5 days to see my ubuntu desktop and now that i see it again i just can't believe how much i missed it

---

### Post by bigken on 2007-01-13
pleased you got it sorted ;)

---

