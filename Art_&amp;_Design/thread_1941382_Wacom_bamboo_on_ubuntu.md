---
title: "Wacom bamboo on ubuntu?"
date: 2012-03-15
forum: Art &amp; Design
---

### Post by p.wolf on 2012-03-15
hey, i just bought the bamboo pen by wacom and dont know how to set it up on ubuntu, i know it can be done but it isnt in the instructions booklet, please advise.:lolflag:

---

### Post by Favux on 2012-03-15
Hi p.wolf,

It depends a bit on what release of Ubuntu you have and which model of the Bamboo Pen (*lsusb* in a terminal).  See the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

---

### Post by p.wolf on 2012-03-15
will it be the same for the bamboo pen and the bamboo pen and touch? 
p.s i want to get it working on ubuntu 11.10

---

### Post by Favux on 2012-03-15
Yes a Bamboo Pen is one of the Bamboo Pen & Touch series tablets.  If yours is the latest it is a third generation BambooPT.  See the "Wacom Bamboo Pen & Touch models".

See the "Release Specific Notes" for Oneiric.

---

### Post by p.wolf on 2012-03-15
okay, thanks i will give it a go : )

---

### Post by p.wolf on 2012-03-15
i recalled that there is a setting in the systems settings for wacom tablets but its not detecting it?!

---

### Post by Favux on 2012-03-15
Right.  Your model is not in Oneiric's 3.0 kernel's wacom.ko (the usb kernel driver/module) because it is so new.  That's why it isn't detected and why you need to compile input-wacom.  Input-wacom will give you a wacom.ko that has your model in it.  I'm assuming it is a third generation Pen.

---

### Post by p.wolf on 2012-03-15
it doesn't say anything about which model it is, all it says is bamboo pen but its the one that is shown on their website. This is quite frustrating.. i dont know what to install.

---

### Post by Favux on 2012-03-15
Open a terminal (enter terminal in Dash).  Then type and enter this command:
```
lsusb
```
In the output will be a Wacom tablet line.  It will look like this:
```
Bus 005 Device 002: ID 056a:00d1 Wacom Co., Ltd 
```
Look at your equivalent of 056a:00d1.  The first 4 numbers are the Vendor ID, i.e. Wacom = 056a.  The second 4 numbers are the Product ID.  
Match the Product ID in the line to the models at the top of the HOW TO.

---

### Post by p.wolf on 2012-03-15
its working, but its hard to use, its moving before the pen touches the pad and its hard to use? o.O

---

### Post by Favux on 2012-03-15
Nice job compiling input-wacom.

Let's look at it.  In a terminal enter:
```
xinput list
```
and post the output.

---

### Post by p.wolf on 2012-03-15
can i get the wacom apps and softwares to run on linux? i want to try the tutorial in particular.

---

### Post by Favux on 2012-03-15
I'm doubtful.  You'd have to use Wine.  I don't think you'd get too far.

The first version of the GNOME Wacom tablet applet is in System Settings in Oneiric.  The next version is considerably improved.

---

### Post by p.wolf on 2012-03-15
i see, i might switch to windows to try out the tutorial! good thing i have a dual boot .
incidentally the eraser wont work and in gimp its not working pressure sensitive, advice?

---

### Post by Favux on 2012-03-15
In Gimp you have to go to Edit > Preferences > Input Devices > Configure Extended Input Devices and set the stylus to Screen.

Does your stylus have an eraser?  If it does point it to the little eraser icon in the tool palette on the left until the eraser is assigned to the eraser.  If it works in the drawing pane then Save it in the tool palette.

---

### Post by p.wolf on 2012-03-15
this is a lot of work, lol 
im going to take a short break and get some food, thank you for all the help until now : )

---

### Post by ofnuts on 2012-03-15
> **p.wolf said:**
> its working, but its hard to use, its moving before the pen touches the pad and its hard to use? o.OThis is standard behavior... when you don't press on the pad, it's like moving your mouse around, and when it touches the pad it's like moving the mouse with the left button depressed.

PS: IIRC my Bamboo one was put to work on Lucid with minimal effort (it was easier than under WinXP...).

---

### Post by sudodus on 2012-03-16
> **p.wolf said:**
> i see, i might switch to windows to try out the tutorial! good thing i have a dual boot .
incidentally the eraser wont work and in gimp its not working pressure sensitive, advice?
It depends what tutorial it is. If it is a pdf tutorial, it's OK, but I don't remember now. However, I remember, that ***I was able to activate pressure sensitivity in gimp*** (years ago, I don't remember if it was in 8.04 or 10.04).

---

### Post by ofnuts on 2012-03-16
> **sudodus said:**
> It depends what tutorial it is. If it is a pdf tutorial, it's OK, but I don't remember now. However, I remember, that ***I was able to activate pressure sensitivity in gimp*** (years ago, I don't remember if it was in 8.04 or 10.04).
Pressure-sensitivity indeed works... but since e are also talking about the eraser tip: in Gimp the stylus and eraser ends correspond to two different pointing tools, which means Gimp keeps a different active tool for each. For instance, the stylus is the Paintbrush and the eraser is the Eraser. However, the eraser tip of the Bamboo isn't pressure-sensitive, so it's not really useful as a pointer for the Gimp Eraser, and the Eraser isn't very useful either in Gimp for advanced users (layer masks do a better job in most cases). So I have never had much use for the eraser tip of my Bamboo.

---

### Post by Favux on 2012-03-16
The eraser on the BambooPT styli is pressure sensitive.  It doesn't move (depress into the barrel) as much physically as the eraser on some of the other styli but it does give pressure sensitivity.

It's just the Pens or Bamboo Ones have a stylus that does not have an eraser.  Unless for whatever reason Wacom decided to include one with his model.

---

### Post by p.wolf on 2012-03-16
turns out it wasn't an eraser just the end and a misleading manual anyway :S
but i dont know how to set up pressure sensitivity in gimp.
I have grown accustomed to the handling though, its a lot easier than it seemed at first!

---

### Post by p.wolf on 2012-03-16
p.s how do i set it up so that the lower pen button pans, like it does in widows?

---

### Post by Favux on 2012-03-16
Like I said in post #15 you need to set stylus to screen in extended input device.

You have the choice of a runtime command i.e. xsetwacom which applies only during a current session or a static configuration Option in xorg.conf.d.  See the Linux Wacom Project mediawiki HOW TO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)  See [Tablet Configuration]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration").

So with Gimp closed to change pressure find your <device name> by entering *xinput list* in a terminal.  It will look something like <Wacom BambooFun 2FG 4x5 Pen stylus>.  Then put it in quotes in the command like so:
```
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen stylus" PressureCurve 0 10 90 100
```
That will give a softer feel.  Then open Gimp and the new pressure curve will apply.  You can determine what something is set to by using get:
```
xsetwacom get "Wacom BambooFun 2FG 4x5 Pen stylus" PressureCurve
```

The "grab" or pan in Gimp or Inkscape is the middle button.  I think the driver does reverse the mapping by default.
```
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen stylus" Button 2 3
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen stylus" Button 3 2
```

---

### Post by p.wolf on 2012-03-16
i have the pressure working, but there is a new problem, when i draw a line say sometimes it randomly goes somewhere i didn't want it to, sort of just creates a peak then goes back to the point i was drawing?

---

### Post by Favux on 2012-03-16
That's the ghost line bug in Oneiric.  There's a PPA that installs a version of Gimp that has a patch to fix the ghost lines.  See the "Ubuntu Release Specific Notes" near the top of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

---

### Post by p.wolf on 2012-03-16
i see, thanks i will check it out

---

### Post by Favux on 2012-03-16
If you haven't done it before adding a PPA is simple and the instructions are on the PPA.

By the way the Wacom and xsetwacom manuals are available through the terminal.  Just open a terminal and enter *man wacom* or *man xsetwacom*.

---

### Post by p.wolf on 2012-03-16
cool, thanks for all the help, it appears to be working properly now and such, i just hope it wont do that thing again it was really quite strange! now i will set up gimp for perfect use with the tablet, starting by making it so i can easily change brush scale! thank you very much for helping me through this: )

---

### Post by thietkelogo on 2012-03-20
Yes, i have used it, it was really hard to use

---

