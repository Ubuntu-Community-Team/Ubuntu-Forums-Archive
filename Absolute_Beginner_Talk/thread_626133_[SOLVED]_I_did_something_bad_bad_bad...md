---
title: "[SOLVED] I did something bad bad bad.."
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by somegirl on 2007-11-28
I installed Gutsy yesterday evening, and got a few important things in order. 

I was working on getting my Radeon Xepress 200M card the right driver (which I found, and will work on once I get what I did fixed). I noticed in the Graphics section under Administration (I think that's where it's at) that it's got the wrong driver installed, so it's reading the wrong card, and won't let me download certain software. That issue aside, I changed the driver, and logged out.

I thought the screen went blank when I logged out. I freaked, and just turned it off (yeah, I know, I know). 

What happened is it changed my screen resolution to one that's way off from what I can see. I know now it was displaying command line login.

And that's the problem, now, when I boot it up, it's the same blank screen, and I know somewhere way off to the bottom left (where I can't see) is a command line login. 

I hope this isn't repetitive, I tried searching around before posting this. 

So I guess the question is, how do it make it boot all the way to the desktop and get it working properly?

---

### Post by Dr Small on 2007-11-28
After it boots, and you see the command line login, login with your username and password, and then run the following command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Dr Small

---

### Post by 00arthuryu on 2007-11-28
Hey, welcome to ubuntu
Where does it go blank?? To which stage does it load up till?
Does Ctrl+Alt+F1
logging in and
```
startx
```
work??

---

### Post by Arthur Archnix on 2007-11-28
If you hti Ctrl+Alt+F1 after starting up the machine you should get a working terminal where you can log in and type 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then go back to the busted terminal (probably F7 or F5) and hit Ctrl+Alt+Backspace to restart X.

Edit: Smalls beat me to it.

---

### Post by Dr Small on 2007-11-28
> **Arthur Archnix said:**
> If you hti Ctrl+Alt+F1 after starting up the machine you should get a working terminal where you can log in and type 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then go back to the busted terminal (probably F7 or F5) and hit Ctrl+Alt+Backspace to restart X.

Edit: Smalls beat me to it.
*Dr Small hurries away in his white frock and the *towel* about his neck :)

---

### Post by scott_g on 2007-11-28
If none of those suggestions work, you could always start up in recovery mode (an option in grub I believe; if you can't get to the recovery mode, you could always use a live CD -- like the Ubuntu install disk....), and restore a backup xorg.conf file (/etc/X11/xorg.conf).  This method is more difficult, but can be explained if the other suggestions do not work....

Just an idea....
Scott

---

### Post by Dr Small on 2007-11-28
> **scott_g said:**
> If none of those suggestions work, you could always start up in recovery mode (an option in grub I believe; if you can't get to the recovery mode, you could always use a live CD -- like the Ubuntu install disk....), and restore a backup xorg.conf file (/etc/X11/xorg.conf).  This method is more difficult, but can be explained if the other suggestions do not work....

Just an idea....
Scott
Yes, that would work, only if you had a Xorg backup, which I am sure, should be in your /etc/X11 directory. But still, since it seems to be a simple Xorg misconfiguration because of the wrong driver, reconfiguring Xorg should help.

---

### Post by somegirl on 2007-11-28
Wow, you guys are quick. 

I'm going to write these things down and reboot in a little while (the things I do in class...) and get back to you guys on what's going on.

To answer a few questions (and add some information), I don't think the system is hanging anywhere. It boots up as though it's going into recovery mode (I assume from what I *can* see) it's just the screen resolution is so far off the prompt is in a place I can't see it. If you try and put in a pass word and hit arrow keys you get those funny characters, right? Well, I can see them if I hit (user name) return, then then arrow keys. 
Oh, and when I hit the power button it says it's stopping loading Gnome. 

As a note, when I did try and install Xorg it told me that it wasn't available for my machine. I tried to install it to get the restricted drivers to install. 

Just FYI:
I'm running a Compaq Laptop Presario V5304 with an ATI Radeon Xpress integrated graphics card, AMD Mobile Sempron Processor (32 bit architecture).

---

### Post by Quash on 2007-11-28
+1 for the Longhorn, 2004 alumnus here.  These guys seem to have you covered.  If you still have a problem and cant solve it, swing by the comp sci lab in the comp sci building, we will be more than happy to get it up and running for ya.  Hell even up in the campus computer store you might be able to get someone there to look at it

---

### Post by somegirl on 2007-11-28
> **Dr Small said:**
> After it boots, and you see the command line login, login with your username and password, and then run the following command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Dr Small

I did this.. and it said it didn't work, but then I rebooted, and here I am typing this on my shiny ubuntu graphical interface. Thank you for your help.

---

### Post by Dr Small on 2007-11-28
Glad to help. :)
Please mark your thread as Solved from Thread Tools so other folks may know to read this thread to find help!

Dr Small

---

