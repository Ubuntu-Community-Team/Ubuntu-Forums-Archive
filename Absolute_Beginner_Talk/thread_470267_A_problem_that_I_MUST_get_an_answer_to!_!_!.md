---
title: "A problem that I MUST get an answer to! ! !"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by mu:te on 2007-06-10
For the past 2 weeks now Ive been in so shitty problems with Ubuntu that Im seriously thinking about going back to Windows!!!

Ive spent almost over 30 hours straight trying to install a properly working driver for my graph card and Ive messed up so badly that now whenever I turn on my computer, the screen goes all black with those -computer letters- and it says Username, after I type in my username it says Password, I type in my password and it just goes like Im using terminal, "User@user $" and to actually load my normal system I have to type in "startx" and than I get this black and white screen, the mouse is just a black X and it takes about 2 minutes to load.

After the load I have no rights to open any Administrator tools, it just says "Unable to copy Xauthorized user"!!!!!!

Im getting so pissed off always being in trouble with LINUX!!!!!

---

Now Im trying to do a complete fresh install of Ubuntu, but since Ubuntu is unable to detect my 'outgoing-hdd' (harddisk outside my computer) Im forced to burn every single file I have to a normal disk.. now let's see, 82gb | 700mb =  118, so Im forced to write 118 disks of files at the 8x speed which will take me few days because Ubuntu is ******..?

So is there ANY freaking way to make fresh install of Ubuntu without removing personal files???

---

Ohh and I for got to say.. When I try to shut down my computer by pressing the red buttin it has no option of shutting down, restarting, and if I press log out I get GDM IS NOT RUNNING!

---

### Post by tdrusk on 2007-06-10
When you pop in the Ubuntu CD there is something that says,"Repair Ubuntu Installation" or something like that. I have never used it, but you might want to look into it.

---

### Post by Rocket2DMn on 2007-06-10
I guess starting with your display is the most important.  I'm assuming you HAVE tried the greatest command ever:
```
sudo dpkg-reconfigure xserver-xorg
```
This should get your display back to normal after you run through the little setup deal.  Make sure you check your correct resolution as this will probably get your display to look more or less how you want it.

---

### Post by mu:te on 2007-06-10
> **Rocket2DMn said:**
> I guess starting with your display is the most important.  I'm assuming you HAVE tried the greatest command ever:
```
sudo dpkg-reconfigure xserver-xorg
```
This should get your display back to normal after you run through the little setup deal.  Make sure you check your correct resolution as this will probably get your display to look more or less how you want it.

Of course I've tried it.. million times, no results!

---

### Post by mu:te on 2007-06-10
> **fuzzyhair said:**
> When you pop in the Ubuntu CD there is something that says,"Repair Ubuntu Installation" or something like that. I have never used it, but you might want to look into it.

Where on EARTH did you see Repair something with the CD?

I downloaded Ubuntu from the website and there is no Repair lalal available with the live cd..

---

### Post by freebird54 on 2007-06-10
A few more details on what you have, and what you tried to do wold help us find a fix.  Certainly we can get you to where you can do something more appropriate than re-backing up everything that way!  So - 

What video card (make - preferably model)
Were you trying different drivers - or trying to get Beryl to run?
Do you know if you had a backup of your /etc/X11/xorg.conf from an earlier (working) state?
Do you still have a Live CD around for working FROM if necessary while fixing?

With those items in hand  - we can get to fixing it all...

:)  (keep smiling - if you can - it makes it go faster)

---

### Post by joe-uct on 2007-06-10
to get "permision" you can log on as root

---

### Post by tdrusk on 2007-06-11
> **mu:te said:**
> Where on EARTH did you see Repair something with the CD?

I downloaded Ubuntu from the website and there is no Repair lalal available with the live cd..
I use the alternate cd, sorry.

Listen to freebird.

---

### Post by logicalmind on 2007-06-11
> **mu:te said:**
> For the past 2 weeks now Ive been in so shitty problems with Ubuntu that Im seriously thinking about going back to Windows!!!

Ive spent almost over 30 hours straight trying to install a properly working driver for my graph card and Ive messed up so badly that now whenever I turn on my computer, the screen goes all black with those -computer letters- and it says Username, after I type in my username it says Password, I type in my password and it just goes like Im using terminal, "User@user $" and to actually load my normal system I have to type in "startx" and than I get this black and white screen, the mouse is just a black X and it takes about 2 minutes to load.

After the load I have no rights to open any Administrator tools, it just says "Unable to copy Xauthorized user"!!!!!!

Im getting so pissed off always being in trouble with LINUX!!!!!

---

Now Im trying to do a complete fresh install of Ubuntu, but since Ubuntu is unable to detect my 'outgoing-hdd' (harddisk outside my computer) Im forced to burn every single file I have to a normal disk.. now let's see, 82gb | 700mb =  118, so Im forced to write 118 disks of files at the 8x speed which will take me few days because Ubuntu is ******..?

So is there ANY freaking way to make fresh install of Ubuntu without removing personal files???

---

Ohh and I for got to say.. When I try to shut down my computer by pressing the red buttin it has no option of shutting down, restarting, and if I press log out I get GDM IS NOT RUNNING!

None of this sounds like a big deal, so try to relax a bit. First of all we need some information from you.

1. What is your video card?
2. What are your internal/external disk layouts and what exactly are you trying to remove/keep.

We're flying blind without more information.

---

### Post by mu:te on 2007-06-11
> **freebird54 said:**
> A few more details on what you have, and what you tried to do wold help us find a fix.  Certainly we can get you to where you can do something more appropriate than re-backing up everything that way!  So - 

What video card (make - preferably model)
Were you trying different drivers - or trying to get Beryl to run?
Do you know if you had a backup of your /etc/X11/xorg.conf from an earlier (working) state?
Do you still have a Live CD around for working FROM if necessary while fixing?

With those items in hand  - we can get to fixing it all...

:)  (keep smiling - if you can - it makes it go faster)

I've tried every single ATi Radeon driver that exist in this world. I've got Ati Radeon X300 64mb graph card. I do have the xorg.conf original file but it doesn't do anything when I replace it with the one that now exists.  I havnt got any idea what Beryl is so no I doubt it. I do have the original live CD in my hands now

---

### Post by iceportal on 2007-06-11
Ubuntu 7.04 is pretty good about automatically detecting/installing graphics card drivers... If you reinstall, try System->Administration->Restricted Drivers Manager. You can check-in your card, and click "OK" and it'll install the drivers it needs automatically. Then just reboot and it should work.

However, if you've already tried this, I'll leave the rest up to the experts here....

---

### Post by Terl on 2007-06-11
Maybe some help here:  [Successful X300 install]("http://ubuntuforums.org/showthread.php?t=321571")

---

### Post by dfreer on 2007-06-11
Let's try to get all the information:

First, post the output of these three commands: 
```
sudo fdisk -l
cat /etc/fstab
cat /etc/mtab
```
Using that as the basis, What is your hard drive and partition layout? Where are your important files located? Is your external drive formatted with NTFS?

We will need to see your current /etc/X11/xorg.conf file, so you will need to post that here. Also it could help to post the output of this command:
```
glxinfo | head
```
to make sure your driver is properly being used.

Next, when you login, do not use startx to start. Use:
```
sudo /etc/init.d/gdm restart
```
If that fails, post the output of this command:
```
cat /var/log/xorg.0.log
```

Also note: it is not ubuntu's fault that ATI drivers suck, that is ATI's fault. Just FYI.
If you don't post this info we can't help you too much.

---

