---
title: "can't install beryl"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by takeitback on 2008-01-16
I've been trying to install beryl for about 2 hours now and I'm getting tired of messing with it altogether.  When I go to Appearance in the visual effects tab, I get the options none, normal, and extra.  After I selected extra, I installed the drivers for my graphics cards, and rebooted. I set my resolution, and here's what I put in the command line and the results that followed.

 sudo apt-get install beryl && install beryl-manager


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package beryl

everytime I try to install it, this is what I get.  If anyone can help me in any way...it would be much appreciated.

thanks.

---

### Post by SOULRiDER on 2008-01-16
Beryl is old. What gives you effects in your current setup is compiz fusion which is compiz + beryl. CF is much newer and better than Beryl. If you want to manage the desktop effects in more detail install this package compiz-gnome
```
sudo aptitude install compiz-gnome
```

---

### Post by SunnyRabbiera on 2008-01-16
> **SOULRiDER said:**
> Beryl is old. What gives you effects in your current setup is compiz fusion which is compiz + beryl. CF is much newer and better than Beryl. If you want to manage the desktop effects in more detail install this package compiz-gnome
```
sudo aptitude install compiz-gnome
```

actually I personally find beryl better then CF in quite a few ways, but most of the features beryl had will probably catch up

---

### Post by Sef on 2008-01-16
To set Compiz-Fusion up, read [Forlong's blog]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion#").

---

### Post by SOULRiDER on 2008-01-16
> **SunnyRabbiera said:**
> actually I personally find beryl better then CF in quite a few ways, but most of the features beryl had will probably catch up

But beryl merged with compiz (merged back actually). What features did Bery have that CF doesnt?

---

### Post by SunnyRabbiera on 2008-01-16
> **SOULRiDER said:**
> But beryl merged with compiz (merged back actually). What features did Bery have that CF doesnt?

well I liked beryl's control functions, it had a really nice control center that was easier to manage then the current setup manager.
I know its effects manager was ported but not its control center.

---

### Post by takeitback on 2008-01-17
I think I've already installed Compiz through an update package, or at least downloaded it. I'm not sure if it installed or not. I did all of this before running the command that I posted earlier. If I have to install Compiz through command line, then it's downloaded but not installed. I don't get a Desktop Effects option in the Prefrences option menu or in the Appearances dialog box.

---

### Post by SOULRiDER on 2008-01-17
those effects youre activating there are actually provided by Compiz Fusion :)
The package compiz-gnome will allow you to fine tune those effects. To install it do
```
sudo aptitude install compiz-gnome
```

---

### Post by Raster_Burn on 2008-01-21
i was trying to install beryl, too. but now you guy smention CF. whats CF? i ran the command you posted and this is what happened: sudo apt-get install compiz-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-gnome is already the newest version.
The following packages were automatically installed and are no longer required:
  libboost-thread1.34.1 libboost-date-time1.34.1 gnash-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


nothing changed...id really like to be able to do all the things ive seen beryl do...

so how do i?

---

### Post by sailor2001 on 2008-01-21
check compiz in synaptics for the manager....if you are in gutsy, you don't have beryl, only fusion.  In comand line, or alt/f2 type'compiz --replace' and to get back to original 'metacity --replace'

---

### Post by bumanie on 2008-01-21
I too would suggest you use compiz-fusion, but if you really want beryl, whart version of ubuntu are you using. I can probably guide you to sites that help with the install on feisty, but not gutsy.

---

