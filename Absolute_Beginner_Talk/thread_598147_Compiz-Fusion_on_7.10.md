---
title: "Compiz-Fusion on 7.10"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by jawknee530 on 2007-10-31
Can someone point me towards a good guide for a newbie that will tell/show me how to install, run, and configure compiz-fusion in 7.10?

---

### Post by macogw on 2007-10-31
It's pre-installed.  I suggest doing the following (copy and paste into the terminal, one line at a time, hitting enter in between):

```

sudo cat "# Fusion-icon PPA" >> /etc/apt/sources.list
sudo cat "deb http://ppa.launchpad.net/maco.m/ubuntu gutsy main restricted universe multiverse" >> /etc/apt/sources.list
sudo cat "deb-src http://ppa.launchpad.net/maco.m/ubuntu gutsy main restricted universe multiverse" >> /etc/apt/sources.list
sudo apt-get update
sudo apt-get install fusion-icon emerald emerald-themes
```

It will install the fusion-icon which can be run by typing ```
fusion-icon
``` (or adding that to your System > Preferences > Sessions > Startup if you want it to be default).  It will also pull in compizconfig-settings-manager which lets you configure Compiz-Fusion.  The Settings Manager will be accessible both through System > Preferences > Advanced Desktop Effects Settings and by right-clicking on the icon.  

The Emerald theme manager and Emerald themes will be installed too.  Emerald Theme Manager will show up in System > Preferences > Emerald Theme Manager and in the right-click menu of the icon, under "Select Window Decorator".  Emerald lets you have the transparent/shiny window borders instead of just the default Metacity themes.

---

### Post by jawknee530 on 2007-10-31
wow, thanks.  i have it up and running and have set up all of my animations.  i can't figure the cube out.  i used beryl back in the day and got the cube running in that but i cant seem to get it up in compiz.

---

### Post by macogw on 2007-10-31
turn on the "cube rotation" plugin

---

### Post by jawknee530 on 2007-10-31
i did.  i only have two workspaces, could that be the problem?  how do i add more?  also i want a dock.  i've seen Avant Window Navigator and think it looks pretty cool.  any advise on that?

---

### Post by macogw on 2007-10-31
In the "General" settings, set "horizontal virtual size" to however many faces you want on the cube

AWN is cool.  There's a HowTo on the forum.  Search for it.

---

### Post by jawknee530 on 2007-10-31
thanks a lot for the help.  i think im gettin the hang of compiz now.  ill look for that how to.

---

### Post by Partyboi2 on 2007-10-31
for awn
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

---

