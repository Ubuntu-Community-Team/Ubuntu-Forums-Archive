---
title: "How to start gnome or KDE?"
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by soendag on 2005-11-12
I just installed ubuntu 5.1. works fine, but starts up with a command line, where I enter user and pass. Then I’m logged in, great.

Question!
How can I start gnome or KDE?
Are these programs installed together with ubuntu?

I am using a
Pentium 166 MHz 
48 Mb ram
1.3 Gb HD


confused!! Yes I am!!

---

### Post by teaker1s on 2005-11-12
yep

---

### Post by kelsey23 on 2005-11-12
[QUOTE=soendag]I just installed ubuntu 5.1. works fine, but starts up with a command line, where I enter user and pass. Then I’m logged in, great.

Question!
How can I start gnome or KDE?
Are these programs installed together with ubuntu?

I am using a
Pentium 166 MHz 
48 Mb ram
1.3 Gb HD


confused!! Yes I am!![/QUOTE]
Uhhhhh, you type:

startx


And, you will have a hard time running even X on that, your system specs are low.

---

### Post by soendag on 2005-11-12
I tried different ways

Type: Startx
Result: -bash: startx: command not found

Type: sudo startx
Result: sudo: startx: command not found

Do you rely think the machine is to small?

---

### Post by kelsey23 on 2005-11-12
[QUOTE=soendag]I tried different ways

Type: Startx
Result: -bash: startx: command not found

Type: sudo startx
Result: sudo: startx: command not found

Do you rely think the machine is to small?[/QUOTE]
Do I think your machine is too small? ahh **YEAH**. I have never installed Ubuntu on a maching with that poor of specs, but it is possible the installer detected them and decided not to install X on their. clearly you have never used *nix before. For future reference, all filename in *nix ARE case sensitive. and you should not need to type sudo before startx

---

### Post by soendag on 2005-11-12
Isn’t there a Linux distribution with an user interface that works on my machine? Or should I use win 95, that works! :eek: 

thanks for helping out

---

### Post by invalid on 2005-11-12
[QUOTE=soendag]I tried different ways

Type: Startx
Result: -bash: startx: command not found

Type: sudo startx
Result: sudo: startx: command not found

Do you rely think the machine is to small?[/QUOTE]

Your machine is not too small, I know several people with roughly the same.
It looks like you installed the server package by mistake, instead of the desktop package.

Try
```
sudo apt-get install ubuntu-desktop
```
or
```
sudo apt-get install kubuntu-desktop
```
to install a graphical enviornment.

Cheers,
Cb

---

### Post by Ampersand on 2005-11-12
Given your specs, I might consider getting xfce (xubuntu-desktop, in the universe repositories).

---

### Post by xequence on 2005-11-12
Fluxbox runs in even 16 mb ram. (I tried it.)

I recomend blackbox though. Its very similar. I use it and I have 192 MB RAM.

---

### Post by Qrk on 2005-11-12
Yes, I you won't be able to run Gnome or KDE. 

type

```
sudo nano /etc/apt/souces.list
```

take out the # in lines with only one of them (they are the addresses)

then you can install xubuntu, which uses a lightweight deskop environment, xfce. Even that might be a little heavy, though. You may want to try fluxbox if you can't get xfce it to work.

```
sudo apt-get install xubuntu-desktop
```

---

### Post by LHZ on 2005-11-12
If Ubuntu doesn't work out for you, you could try [Damn Small Linux]("http://www.damnsmalllinux.org") or [Puppy Linux]("http://www.goosee.com/puppy/"), both of which have been optimized for small size and compatibility with older hardware. Damn Small is 50 MB total, Puppy somewhat over 60. Both have a full blown graphical interface, office software, browsers and other basic needs. I've ran Damn Small myself, and it's blazing fast.

---

### Post by kelsey23 on 2005-11-12
Try XFCE. Even though your specs are probably even too low for that, it is great. I have fine specs, and I use it because I like the UI.

---

### Post by marksi on 2005-11-12
There's some easy installation instructions for xubuntu
at [https://wiki.ubuntu.com/InstallingXubuntu](https://wiki.ubuntu.com/InstallingXubuntu)

---

