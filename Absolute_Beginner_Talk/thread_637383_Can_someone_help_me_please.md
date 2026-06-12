---
title: "Can someone help me please"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Jgryder on 2007-12-10
ok I am a newbie linux user well I managed to get this far at least

I saw a video of a ubuntu desktop and the compiz fusion cube, please be patient with me
I am sure you all have heard this 1000 times before, but I can't find a thread that explains it well enough that I could understand it,

link for the video  [http://www.youtube.com/watch?v=q_wL2nCpFOE](http://www.youtube.com/watch?v=q_wL2nCpFOE)

so I want to know how in detail what I need to install and what the programs are called

I have compiz fusion, and ubuntu 7.10.

example  what is that thing at the very top on his desktop?

how do you get pictures on the cube, I have tried putting different pictures but with little results, I think I might have the settings a tad bit out of whack.

I saw another pictures with what seemed to be widgits but I could only find gdeskets which didn't seem to work very well,

what is screenlets  how can I get it?

what is avant?  how can I get it?

and if there is another thread that explains all I request to know, please point me to it.

so if your kind enough to help me thank you, if not  thank you anyway.

---

### Post by markusf21 on 2007-12-10
```
sudo apt-get install compizconfig-settings-manager
```
in a terminal should get you started. This is the advanced settings manager for Compiz.
You can find it under System --> Preferences --> Advanced Desktop Effects Settings

---

### Post by Partyboi2 on 2007-12-10
have a look at this  for Avant
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)
[http://wiki.awn-project.org/index.php?title=DistributionGuides](http://wiki.awn-project.org/index.php?title=DistributionGuides)

To get themes for compiz I suggest 
[http://www.gnome-look.org/](http://www.gnome-look.org/)
This might help with compiz as well
[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

Screenlets look here:
[http://compiz.org/Desktop_Screenlets](http://compiz.org/Desktop_Screenlets)
[http://tombuntu.com/index.php/2007/08/24/osx-like-widgets-with-ubuntu-screenlets-and-compiz-fusion/](http://tombuntu.com/index.php/2007/08/24/osx-like-widgets-with-ubuntu-screenlets-and-compiz-fusion/)

hope this gets you started any problems ask as you go :)

Edit: For kiba dock [http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)

---

### Post by ncappel1 on 2007-12-11
The bar used on top of the screen is actually not avant, it is Kiba-dock. it uses the akamaru engine to make the icons fly about.

For different pictures on the cube, do you mean different wallpapers for each side of the cube? if so, that is possible, but the trade-off is that you have to disable the nautilus desktop, which means you can't have folders/files on the desktop.

I personally don't like to use the widgets, but in conjunction with the "widget layer" plugin from compiz fusion, you can get the "dashboard" effect like on a Mac computer. 

just for kicks, you may want to check out conky, it is hours of tweaking fun.

---

