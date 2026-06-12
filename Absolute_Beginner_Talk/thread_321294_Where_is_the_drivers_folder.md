---
title: "Where is the drivers folder?"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by some_random_noob on 2006-12-18
Not that I'll be changing anything for my 17 inch lcd :D 

I'm basically looking for anything that controls my monitor, mainly drivers... thanks in advance 8)

---

### Post by Shatrat on 2006-12-18
Well there isn't really a drivers folder...there is a config folder which is basically /etc/
Drivers and configuration stuff are two seperate things (even though they are often bundled together).

If you want to change some setup for your display then you need to use whatever config utility exists for your device.  ATI and nVidia have different config programs that you can use to adjust brightness and such.  There is also a tool to change your resolution in the System menu.

---

### Post by some_random_noob on 2006-12-18
Well I'm trying to find what crappy piece of code keeps changing my refresh rate back to 75hertz when I run my game or other applications, when its normally 60. Any system thingy thats runs in the background that does this? It could even just be how it starts stuff up.

---

### Post by pormogo on 2006-12-18
try checking out /etc/X11/xorg.config

---

### Post by Sandlst on 2006-12-18
Normally, I believe X sets your monitor's refresh rate on a range (eg. 60-75).  To get around this, run the following command (Applications/Accessories/Terminal)```
sudo dpkg-reconfigure xserver-xorg
```It will then precede to ask you a bunch of questions about your system.  If you don't know something it asks, it is usually safe to leave the default entry in, and just hit ok.  Near the end, it will show three options for setting up 'best' refresh rates and resolutions.  You will want to goto the most advanced (Expert I believe) option, where you can specify a single refresh rate, hopefully forcing X to use this single refresh rate only (Note that if your monitor is not meant to run on a refresh rate, it could [COLOR="Red"]permanetly damage your monitor and/or video card![/COLOR] so please be careful).  Also note on the step before this, it will ask you which resolution(s) you want the x server to use.  In this screen, your computer will not be able to change the resolution to anything you dont select (unless you de-select them all) and since some programs/games require you to change your resolution, I would recommend selecting all of them your monitor/video card is capable of producing.
If something goes wrong, you will have a backup xorg.conf file in /etc/X11/ that reads something like xorg.conf.backuptimeanddategoeshere.  So if you have problems, to restore your settings, use the command ```
sudo cp /etc/X11/xorg.conf.[COLOR="Lime"](**HIT TAB HERE**)[/COLOR] xorg.conf
```Hitting TAB should auto-complete the filename for you. I've never tested to see if this method will in fact solve your problem, but I hope it will, good luck :).

---

### Post by some_random_noob on 2006-12-18
Ah, thanks Sandlst, that looks like something worth checking out.

> if your monitor is not meant to run on a refresh rate, it could permanetly damage your monitor and/or video card!
What do you mean by "not meant to run on a refresh rate" is that a monitor that is only set to one refresh rate? Like tv screens or something?

---

### Post by some_random_noob on 2006-12-18
Ah, thanks Sandlst, that looks like something worth checking out.

> if your monitor is not meant to run on a refresh rate, it could permanetly damage your monitor and/or video card!
What do you mean by "not meant to run on a refresh rate" is that a monitor that is only set to one refresh rate? Like tv screens or something?

edit- and what do I do when I've typed "sudo dpkg reconfigure xserver-xorg"? Its confusing :mad: And I'm also a 16 yearold noob. All I get is this:

> noob@host:~$ sudo dpkg reconfigure xserver-xorg
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

---

### Post by ibanez on 2006-12-18
You are missing a hyphen in the above command try this

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Sandlst on 2006-12-18
Errr yes Ibanez is correct, my bad.  As for the sync rate, there is a warning I remember reading a while ago when I had to do this myself.  I cant recall exactly where it came from, but I would rather err on the safe side.  You should be able to find a list of acceptable sync rates in your monitors manual, or perhaps online.  Either way, I would check to be 100% sure that it won't mess anything up before doing this.

---

### Post by macogw on 2006-12-18
> **some_random_noob said:**
> Ah, thanks Sandlst, that looks like something worth checking out.


What do you mean by "not meant to run on a refresh rate" is that a monitor that is only set to one refresh rate? Like tv screens or something?

Well, if your monitor is only *capable* of 60-75 for the refresh rate, and you force it to do 40, it'll damage the hardware.

---

