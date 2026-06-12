---
title: "Re-Install ?????"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by darren1270 on 2007-05-09
I just upgraded my video card to nvidia geforce fx5200 and when I tried to boot into ubuntu on a duel boot system with winxp I have a screen with all kinds of things on it saying something about xorg????   Can I just dpackage or whatever it is called to get back up and not have to re-install??

Thank you in advance.  

BTW can you tell I am a newbie with linux and Ubuntu?  LOL

---

### Post by Terl on 2007-05-09
First, what did you upgrade from?  Was it also an nvidia card?

Do ```
sudo dpkg-reconfigure xserver.xorg
```

If the answer above is no, then pick nv as your driver when asked about your graphics card.  If you had installed an nvidia driver and it will work with the fx5200 pick nvidia instead (nvidia will not be a choice if you did not install the driver before - we can deal with that later)

Make sure you have the info on your monitor.  If you do not don't use the advanced when configuring the monitor.  Use the simple one.

---

### Post by darren1270 on 2007-05-09
Upgraded from onboard graphics .... this if I am running off the live cd?

---

### Post by Terl on 2007-05-09
Run the code I gave you from the text screen (you are in text mode, right?  the x server would not start...).  The command I gave earlier will start a routine with a series of questions in ncurses (looks graphical).

---

### Post by bill602 on 2007-05-10
Greetings,
I'm having a similar problem to the one that Darren1270 is describing.  I have an Nvidia card in addition to the original video that came with the computer.  That allows me two monitors.  When I installed the Nvidia driver that Ubuntu downloaded, it seems to have disabled my GUI.  I tried the command you suggested above, but it says xserver.xorg is not installed.

Can you help getting the GUI turned back on?

Bill602

---

### Post by zvacet on 2007-05-10
```
sudo dpkg-reconfigure xserver.xorg
```

Try to replace **nvidia** with **nv**

---

### Post by bill602 on 2007-05-11
zvacet,
I entered the command you suggested.  The message I received back said that Package 'xserver.xorg' is not installed & no info is available.  How do I replace 'nvidia' with 'nv'?

Bill602

---

### Post by zvacet on 2007-05-11
If you use GNOME

```
sudo aptitude install ubuntu-desktop
```

and if you prefer KDE

```
sudo aptitude install kubuntu-desktop
```

---

### Post by Cheese Sandwich on 2007-05-11
I just did a search for "xserver" in the synaptic package manager. There's a bunch of stuff there, including:

xserver-xorg
xserver-xorg-core
xserver-xorg-video-nv

...etc.

On my laptop, all of the above & a bunch more (nearly all the xserver-xorg-video-*, for example) were installed automatically on installation. Try going into synaptic & installing these.

---

### Post by gsiliceo on 2007-05-11
I have the same problem as Darren1270, i was using integrated graphics with ubuntu just fine, and then upgraded to a Nvidia Fx5200, ubuntu wasnt loading anymore, in recovery mode i could see the boot process stopping and sending some weird messages about xorg. It doesnt give a command line, just stops.

---

### Post by Najand on 2007-05-11
It is NOT: 
```
[COLOR="Red"]sudo dpkg-reconfigure xserver.xorg[/COLOR]
```
it is:
```
[COLOR="Blue"]sudo dpkg-reconfigure xserver-xorg[/COLOR]
```

---

### Post by zvacet on 2007-05-11
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

