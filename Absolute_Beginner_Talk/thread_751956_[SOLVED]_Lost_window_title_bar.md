---
title: "[SOLVED] Lost window title bar"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by C!pheR on 2008-04-11
Ok, I'm certain this should be reletively easy to fix...

I've fitted a new gfx card (Nvidia 6200), booted up the computer and used the following commands to install the card:

```
sudo apt-get update 
sudo apt-get install nvidia-glx 
sudo apt-get upgrade 
sudo dpkg-reconfigure xserver-xorg 
```

Reconfigured X server and rebooted. All seems to be fine, except when I open any window I have no title bar (the bar with the minimise, full screen and close buttons)! I also cannot properly open a terminal window; when the terminal opens all I get is a white screen that does not respond to any commands.

Any ideas?

---

### Post by SunnyRabbiera on 2008-04-11
you may need to turn effects off, compiz can have issues like this

---

### Post by rasmus91 on 2008-04-11
which desktop performance are you using? (you know; effects high,low or medium?)

---

### Post by goiggles on 2008-04-11
This is most likely an effects setting. However you should be able to get your titlebars back by reloading metacity you can do this by pressing alt+F2 and typing metacity in the box.

---

### Post by C!pheR on 2008-04-11
Tried on "None" and "High", same problem regardless. Running metacity has made no difference.

***EDIT*** tried changing back to "None" and running metacity, seems to have done the trick

---

### Post by erginemr on 2008-04-11
> **C!pheR said:**
> Tried on "None" and "High", same problem regardless. Running metacity has made no difference.

***EDIT*** tried changing back to "None" and running metacity, seems to have done the trick

But then, you lose the desktop effects, so this is only a temporary workaround.

Please refer to here to see if the suggestions therein help your cause:

[http://ubuntuforums.org/showthread.php?p=4695440](http://ubuntuforums.org/showthread.php?p=4695440)

---

### Post by erginemr on 2008-04-11
I have just added  a new post (#5) to that page:
[http://ubuntuforums.org/showthread.php?p=4695440](http://ubuntuforums.org/showthread.php?p=4695440)
also for you try. 

I also suggest you to remove the mark [SOLVED] from your title for the time being (if you can), to attract more forum people to help.

---

### Post by Znort_Ubern00b on 2008-04-11
try typing this into terminal when running metacity

sudo nvidia-xconfig --add-argb-glx-visuals -d 24

it worked for me and i had the min max and close buttons back...

---

### Post by C!pheR on 2008-04-13
> try typing this into terminal when running metacity

sudo nvidia-xconfig --add-argb-glx-visuals -d 24

it worked for me and i had the min max and close buttons back...

Just tried this, after <CTRL + ALT + BACKSPACE> to kill X, seemed to work a treat. Now desktop effects are working with the title bar, thanks :)

---

