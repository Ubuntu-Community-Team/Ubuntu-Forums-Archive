---
title: "ubuntu or fedora"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by em11488 on 2007-08-04
I know this an ubuntu forum, but my only question regarding the choice is the compatability. Ubuntu never works on my system (HP dv6000z, amd x2 2.0 ghz , geforce go 7200). Im wondering if fedora could possibly boot everytime I go into it from grub, because usually ubuntu just goes to a black screen. So, would fedora be a good try for a system that doesnt work right with ubuntu?

---

### Post by Brunellus on 2007-08-04
I don't understand the question.  are you using fedora now?

---

### Post by Elemental_TJ on 2007-08-04
I've never actually used Fedora and therefore have no experience
with it. I've heard that Fedora has many more drivers as Ubuntu has.
I would recommend you try Fedora and see how it works with your
system. If it doesn't, come back and I'll suggest another Linux OS. :)

---

### Post by em11488 on 2007-08-04
is fedora a distro of linux that would be more compatable with my system than ubuntu.

---

### Post by Brunellus on 2007-08-04
> **em11488 said:**
> is fedora a distro of linux that would be more compatable with my system than ubuntu.
unknown.  Try a live CD and see how it runs.

Your main trouble will be the display driver, however.  I'm surprised that you can't even get a plain VGA display mode on your Ubuntu install.

---

### Post by em11488 on 2007-08-04
should it automatically go to vga screen if soemthings wrong? Or are there steps to get that to work

---

### Post by Elemental_TJ on 2007-08-04
I use an 8600GT and I thought I had the same problem.
Are you running from the LiveCD? If so, press F4 when
it shows you the title screen asking if you want to install.
Select a resolution and then select install. It worked for
me. Now that I have Ubuntu installed, the screen is only
blank when Ubuntu is loading.

---

### Post by Brunellus on 2007-08-04
> **em11488 said:**
> should it automatically go to vga screen if soemthings wrong? Or are there steps to get that to work
I can't remember if "bulletproof X" is implemented in Feisty.  If not, your black screen is NOT death--it's the command line, where all proper work is done.

Log in, and then 

```

sudo dpkg-reconfigure xserver-xorg

```

Follow the prompts but be sure to select VESA as your display driver.

Note that this is the lowest-common-denominator method of getting you a working GUI;  but once you're up on the GUI you can make use of the (quite nifty) restricted-drivers tool in Ubuntu, which may (hopefully) have a better driver for your graphics card.

---

### Post by em11488 on 2007-08-04
how do I login if the screen is black?

---

### Post by Brunellus on 2007-08-04
> **em11488 said:**
> how do I login if the screen is black?
do you see *any* text at all?  

When X fails, you should be taken to a command-line, which is mostly black, with little white letters.

---

### Post by em11488 on 2007-08-04
no, its just black, nothing blinking, nothing at all

---

### Post by joao82 on 2007-08-04
my brother had the same problem with his HP. in the grub menu you have to set the VGA option to a low value. i don't remember very well how we solved it. but after getting in with a low resolution you can download the correct drivers.

---

### Post by joao82 on 2007-08-04
and fedora is much worse on hardware compatibility. the Fedora Core 5 dvd wasn't even recognized by that laptop

---

### Post by anewguy on 2007-08-04
When you boot Ubuntu and eventually the black screen shows up (I assume you can see the text during boot but then have a black screen after that?), try holding down ctlr alt and press F2, then release the keys.  If it comes up to a log on screen, then the problem is your video drivers (most likely case anyway).  If so, post back here and we'll try to walk you through the rest (I hope!!):)

---

### Post by ThrobbingBrain66 on 2007-08-04
> **joao82 said:**
> and fedora is much worse on hardware compatibility. the Fedora Core 5 dvd wasn't even recognized by that laptop

I don't know how accurate that statement is right now.  Fedora is currently in version 7.  I tried Fedora just after 7 was released and it detected everything that Ubuntu did and more (screen dimming worked, doesn't in Ubuntu).  I didn't care for Yum and a few other things however, and stayed with Ubuntu.

---

### Post by joao82 on 2007-08-04
sorry, I meant FC6 didn't worked. my mistake. FC7 got out one week before  we bought the HP and i still hadn't downloaded the dvd to try it on that laptop.

---

### Post by gabhla on 2007-08-04
Suggust posing Fedora questions on their Forum which, like Ubuntu's, is very big and supportive.  I have Fedora 7 on this pc, finally got around to trying it out.  Fedora is great, it's very similar to Ubuntu.  The default desktop environment is Gnome, although KDE is available, (I used Gnome),   No problems, so far.

In general, Fedora is a tad more complicated.  I figured it all out, so it can't be too bad.  Not as newbie friendly as PCLOS or Linux Mint, and less friendly then Ubuntu mainly due to getting used to yum - their package manager, (although there is a gui available).  There is no "Automatix", or anything similar.

---

