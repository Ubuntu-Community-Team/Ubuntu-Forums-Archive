---
title: "Selecting ATI driver"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by mect on 2006-07-15
Maybe I'm mistaken, but I believe these drivers are included in the kernel.  I want to give Ubuntu a try (I've been using Kubuntu).  With KDE, you can go to system settings -> Display and select the driver you wish to use.  While I'm aware this can be accomplished through the command line and editing xorg.conf, I was wondering if Gnome has a way of doing this through the GUI.  I've searched, but haven't found anything.

---

### Post by verbatim210 on 2006-07-15
is your ati drivers working okay?  i cant seem to get my resolution to focus with my monitor ie. the display goes outside of the screen.
downloaded ati(linux) driver last night, couldn't get it installed.  when i tried...
sh ./ati-driver-installer-8.26.18-i386.run 
it gave me an error message, cant remember what it was.

---

### Post by catlett on 2006-07-15
Do you want the latest ati drivers or something specific? 
This is how I install ATI drivers for my ATI Radeon 9600 following the Daper Guide [http://doc.gwos.org/index.php/DapperGuide#Installing_the_driver_.28ATI.29](http://doc.gwos.org/index.php/DapperGuide#Installing_the_driver_.28ATI.29)
You have to have "restricted" enabled in your repository list for this to work.
```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) [COLOR="Red"]#Okay if it is already installed[/COLOR]
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```
The phrase in red doesn't have to be entered. It is just the authors way of letting you know it is OK if the command returns "already installed"

---

### Post by verbatim210 on 2006-07-15
okay okay i confess, i wasn't using ubuntu.  i was trying out SUSE last night, my ubuntu ati drivers are fine [-(

---

### Post by mect on 2006-07-15
I believe I confirmed that I have the module for the ati driver installed (linux-restricted-modules), it is just figuring out how to select this driver using gnome (if there is a way) or if I have to do this through command prompt (which is fine).  I'm mainly interested in getting to know my way around in gnome, and this is the main thing I can't figure out how to do in gnome that I could in kde.

---

### Post by catlett on 2006-07-15
Good luck with Suse. I never got a good install in 4 tries, I just gave up. The best configuration I got was with Opensuse Slick. Even then I didn't get it working perfect but at least it didn't freeze all the time.
I can't help with ATI in suse because I had nvidia then.
The issue with ATI is they don't release any code for linux, whereas nvidia releases linux drivers.

---

### Post by verbatim210 on 2006-07-15
what do you mean ati doesnt release code? what code?
your right suse is problematic but you know, curiosity...

---

### Post by catlett on 2006-07-15
What I meant was they have a driver but itr is proprietory. They don't release all of the source code so others can see how it is written and then tweak it or make it work on other non-supported cards.
Here's ATI's reply to the question
> 	Is complete driver source code available? 
A4:	Some of the technologies supported in our driver are protected by non-disclosure agreements with third parties, so we cannot legally release the complete source code to our driver. It is NOT open source. We do, however, include source code for the control panel and certain other public segments. We also actively assist developers in the Open Source community with their work, so if you absolutely require an open source driver for your graphics card, we can recommend using drivers from the DRI project, Utah-GLX project, or others.

---

### Post by catlett on 2006-07-15
Back to the original issue. KDE is more configurable than gnome. That is why Linus recommends KDE over gnome. (In fact he hates gnome and calls their devs "gnome nazis")
I do not know how to select the driver other than editing the xorg.conf file. I just follow the dapper guide to tell you the truth.
All I know are a few commands to verify my card is running correctly.
```
lspci | grep ATI
```
```
fglrxinfo
```
```
glxinfo | grep render
```
```
glxgears
``` If I find anything, I'll post.

---

### Post by mect on 2006-07-15
Thanks, that is what I wanted to know.  I've got it working, but mainly was interested in getting to know gnome better.

---

