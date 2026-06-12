---
title: "Easy System Cleanup?"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by whitenerdy92 on 2007-11-21
Is there an easy way to improve the performance of my system without buying new hardware (like some sort of disk cleanup utility)? My system freezes up alot (i only have 512 mb ram and i multitask alot), but before i buy more ram id like to know if i can improve performance more easily?

---

### Post by louieb on 2007-11-21
Sure its doable, but compared to adding ram  its  not easy.   Just go to the **Tutorial and TIps **section and do a search on speed. 
#1 forget Gnome and install Fluxbox.   
[http://ubuntuforums.org/showthread.php?t=483613&highlight=fluxbox](http://ubuntuforums.org/showthread.php?t=483613&highlight=fluxbox)

Get rid of unneeded services on startup. 
[http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651)    

You'll have to do configuration changes and the chance to break your system is real. (make a backup).  

For my time and money I'd rather  buy some ram. But now I have  getting Fluxbox configured just the way I want it - as my  favorite time waste.  Have fun.

---

### Post by shearn89 on 2007-11-21
It may not be your hardware - depending on what you're doing when it freezes. There are a couple of bugs reported on launchpad about the new gutsy kernel freezing: one seems to be connected to ndiswrapper and can be sorted by upgrading to 1.49, and another is to do with the kernel. They tend to show themselves when downloading torrents or using ntfs file systems...

---

### Post by whitenerdy92 on 2007-11-22
Yeah, I'm probably gonna get some ram soon, hopefully that will help.
Fluxbox might help, but I still like the look and feel of gnome :] but i might give it a try.
As for possbily being something more serious, that's what im looking for some utility to check my os for errors. some other problems iv been have is that i can only access the internet with Pidgin, sometimes when i use konqueror or firefox it takes unbelievable long to load, or not at all. When i logout and log back in its fine, but its still annoying. And sometimes I don't know if the problem is a serious bug, or just some random fluke. Still, 512 megs of ram sure aint helping!

---

### Post by whitenerdy92 on 2007-11-22
btw i tried flux, even though its fast im a newbie and i need something less minimalistic, sry

---

### Post by philinux on 2007-11-22
It's running damn fine for me so I doubt it's the memory.

---

### Post by whitenerdy92 on 2007-11-22
Exactly what my thinking is (but extra memory can't hurt).
Unfortunately, I lack the knowledge to diagnose any problems, and the problems aren't consistant enough to file a bug report. That's why I'm looking for something to check for errors.

---

### Post by philinux on 2007-11-22
Two things,

Run system monitor and check the processes tab to see if anything hogging system like trackerd, which can be turned off.

Or in a terminal type top and look there too. This method uses less cpu power.

---

### Post by whitenerdy92 on 2007-11-23
I've used that method, but things still turn on next time I log on. I think I heard that theyrs a way to make processes not start on startup... anyone know how?

---

### Post by forestpixie on 2007-11-23
depends on what you want to stop i suspect

---

### Post by whitenerdy92 on 2007-11-23
Well... taking a quick look at the system monitor...

trackerd
beagled
beagled-helper
gnome-screensaver
evolution-alarm-notify

and possibly anything else someone thinks just drags down your computer that starts up when u log  on

---

### Post by forestpixie on 2007-11-23
Well some are in sessions - in the system preferences menu, you could also look in services - carefully :) - in system admin menu.

But I don't believe I've got beagle so not sure about that - if you're not using it and it's slowing you down uninstall it

---

### Post by whitenerdy92 on 2007-11-23
Thanks, that worked, but as if my day couldn't get any more stressful...
1. Occasionally, a few minutes after I log on, only Pidgin lets me use the internet, firefox and konqueror don't load, the bar stays empty.
2. Last time I ogged on, my desktop showed nothing but black, no background, no icons, and my CPU was hot as hell and running like a runaway train.
3. So, I restarted my computer, only to find my annoying-yet-helpful diskcheck that i get every 30 times i boot up (thats what i was looking for! a way to do that sometime other than every 30 times).
4. It says my operating system has too many errors and cannot be booted (!!!)
5. I get the terminal, it told me to run fdsk (or something like that), then I pressed CTRL-D to restart
6. System restarts, desktop works, and here I am
Anyone have a clue to what that means? (Oh, and also, I realized that I have firestarter, maybe that's what is making my internet not work?)

---

