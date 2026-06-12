---
title: "install help"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by rede2learn on 2007-10-29
Well I downloaded ubuntu 7.10.  Burned the iso, loaded it into my drive and booted from the cd drive.  I get the first window, select install ubuntu.  Then there is another ubuntu screen with a progress bar.  The bar fills all the way and now my screen is black and I can't do anything.  SHould I just wait longer or do I need to do something else during the install?  
I really want to try Linux but I can't seem to get any to install properly.  
Please Help.

---

### Post by oilchangeguy on 2007-10-29
please provide your computers specs.

---

### Post by rede2learn on 2007-10-29
Dell 
Intel pentium 4
266-mhz ddr sdram
Intel integrated AGP graphics
sony dvd rw drive


This computer had xp in it for the entire history, about 5 years.  I want to wipe that out and use ubuntu before I reinstall the old os.  

What else do I need to provide?

---

### Post by oilchangeguy on 2007-10-29
> **rede2learn said:**
> Dell 
Intel pentium 4
266-mhz ddr sdram
Intel integrated AGP graphics
sony dvd rw drive


This computer had xp in it for the entire history, about 5 years.  I want to wipe that out and use ubuntu before I reinstall the old os.  

What else do I need to provide?

the problem is your ram (or lack of) you typed 266, i'm sure you mean 256. and if the computer has on board video it's taking some of that. ram's cheap i'd suggest an upgrade. this will improve the performance of whatever operating system you use. your computer probably will support 1gb of ram, 512x2.

---

### Post by Maestro23 on 2007-10-29
You might be able to squeeze a lighter distro onto that machine.  Perhaps Puppy Linux or DSL (Damn Small Linux). I don't know if Xubuntu would even work on that setup.

---

### Post by rede2learn on 2007-10-29
Thanks.

---

### Post by houstonbofh on 2007-10-29
You can install with the alt-install CD.  I have several 256 meg machines, and they run fine.

---

### Post by rede2learn on 2007-10-29
How do I do that?  Is there an alternative place to download?

---

### Post by unisol on 2007-10-29
yes download it from the same place. you could also try safe graphics mode  on the live cd,when you load the cd.

---

### Post by rede2learn on 2007-10-30
Safe graphics mode didn't work.  Some error about the x drive not working.  I think it was the x drive.

---

### Post by hyper_ch on 2007-10-30
actually, the ram amount is so far untold... it's 266mhz ddr ram ;)

---

### Post by rede2learn on 2007-10-30
I used the alternative cd and the text install was super easy.  Now I have a great looking orange screen but can't do anything.  I've watched a bunch of youtube vidoes of how to open applications but they keep clicking a button on the top of their screen.  I have no buttons.  Just the orange screen.  What do I do now?  I've read about how to use cli to open apps but I am not sure how to open the terminal.  Is that what opens when I hit ctrl+alt+f2?

---

### Post by legonum on 2007-10-30
Have you found the applications folder on your Gutsy Gibbon desktop, and are the workspace icons displayed? 

I ask what I do for two reasons,
First: It sounds like there may still be a problem with your display.

Second: I'm cursed with curiosity.
I Haven't seen Gutsy Gibbon yet, and I'm wondering if it's desktop is like Feisty fawn's. I had a devil of a time finding anything on it ("it" being Feisty Fawn) at first, since all the shortcuts were hidden. I'm embarrassed to think how long it took me to find the drop-down shortcut menus that open from the hidden bar on the upper left corner of the desktop. Being totally unfamiliar with Ubuntu/Linux and how they generally work, even such simple things can kill the user experience for some of us before we ever get it started. Now that I know how to find some of my applications I like the clean, uncluttered look of my desktop....but it's very hard for a total newbie to figure out there's anything to find there without visual clues. Unless they've had some warning it can feel like an intentional "dirty trick", as though someone's purposely designed an OS that won't let them find their working applications.

---

### Post by rede2learn on 2007-10-31
Thanks for the reply.  I have tried clicking in all areas of the desktop.  Corners all along the top.  There are no icons on the desktop at all.  If I right click on the desktop I have some options such as: change background, create launcher, and maybe open file, but I don't have any files yet.

I was thinking last night that maybe in isntallation I messed up my resolution on the monitor.  In the set up mode there was a section where you could pick the resolutions you wanted ubuntu to run in.  When I tried to select a few I accidentally hit return and the installation continued without me selecting a resolution.  So my desktop does have a border around it that is solid black. Maybe there is part of the desktop I can't see and therefore can't access with my mouse so that I can open up the drop down menus.

---

### Post by overdrank on 2007-10-31
> **rede2learn said:**
> Thanks for the reply.  I have tried clicking in all areas of the desktop.  Corners all along the top.  There are no icons on the desktop at all.  If I right click on the desktop I have some options such as: change background, create launcher, and maybe open file, but I don't have any files yet.

I was thinking last night that maybe in isntallation I messed up my resolution on the monitor.  In the set up mode there was a section where you could pick the resolutions you wanted ubuntu to run in.  When I tried to select a few I accidentally hit return and the installation continued without me selecting a resolution.  So my desktop does have a border around it that is solid black. Maybe there is part of the desktop I can't see and therefore can't access with my mouse so that I can open up the drop down menus.

Hi when you reach the blank screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by rede2learn on 2007-10-31
Thanks in advance.  Everyone in this community has been very helpful.  One of the reasons to switch to Linix!

---

### Post by rede2learn on 2007-10-31
Well that did end up working.  My screen is now shifted down to the left corner but I can access the top tool bar.  I guess I should just keep picking different resolutions until I get one that looks the best.


Thanks again for all of the help.

---

### Post by overdrank on 2007-10-31
> **rede2learn said:**
> Well that did end up working.  My screen is now shifted down to the left corner but I can access the top tool bar.  I guess I should just keep picking different resolutions until I get one that looks the best.


Thanks again for all of the help.

Hi and glad to hear it worked. Is this a desktop because you can adjust your monitor some to correct your screen. If all is working could you mark the thread as solved under the thread tools. Good Luck!

---

