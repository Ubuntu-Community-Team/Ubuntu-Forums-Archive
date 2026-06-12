---
title: "MASSIVE problem with flash plugin in firefox"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by dumi on 2006-11-27
1st day of usin linux. woo hoo.  but..  i cannot open any internet pages with flash on them. the 1st flash site i tried to open, gave me a popup sayin u need to install plugin(flashplayer) to view the site. i downloaded the plugin, and am running the installer, but wen i go bak into firefox, and look unnder plugins, the flash player isnt showing up..   A MORE SINISTER PROBLEM is everytime i open a flash website, or a site with any flash based ads, e.t.c, firefox just dies.. it just cuts out, and i'm not even getting that u need to download plugin..screen anymore.. i dunno whats going on,  but this is now a biig problem for me as most sites have flash in them, so  cant do anything..  HELLPP pleease..  am using edgy. and i think its the latest firefox version too (came with edgy)

---

### Post by adam.tropics on 2006-11-27
I don't know which way you went about getting flash, but you might want to try here...
- [flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb]("http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb") (Firefox Plugin)

---

### Post by lyceum on 2006-11-27
Flash 8 does not work with Linux, and the alternets seem buggy. There is a flash 9 beta getting great reviews, but it is beta, so I am not sure if you really want to use it. If you do, try [http://www.getautomatix.com/](http://www.getautomatix.com/) It is not supported, but the flash works great for me. Jsut follow the tutorial and click on the Flash 9 once up.

---

### Post by lori.ann on 2006-11-27
This is the exact same thing that happened to me (I just installed flash today too, from the adobe website my browser sent me to, and just clicking on a link to go to a flash page shuts down the whole browser).
I'll try out the flash 9 beta and report back.

---

### Post by lori.ann on 2006-11-27
A great install HOW-to is available at [http://www.ubuntuforums.org/showthread.php?t=279990](http://www.ubuntuforums.org/showthread.php?t=279990).

---

### Post by AndyCooll on 2006-11-27
This is a known bug with FF and if you search on these forums you'll find a number of workrounds. What worked for me was to type into the command line the following:

```
sudo gedit /etc/X11/xorg.conf
```

I then found the "DefaultDepth" line and changed the setting to 24. I then restarted X (or it might be easier for you to restart your pc) and the problem was solved!

:cool:

---

### Post by three-cushion on 2006-11-27
> **adam.tropics said:**
> I don't know which way you went about getting flash, but you might want to try here...
- [flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb]("http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb") (Firefox Plugin)

Hello:  I run Ubuntu on a Mac (Tiger 10.4.8) Don't think an i386 download will help me.. fact is, I get an ERROR  that it is not..
Have another URL for me to try?

Cheers, Jim B

---

### Post by wpshooter on 2006-11-27
> **dumi said:**
> 1st day of usin linux. woo hoo.  but..  i cannot open any internet pages with flash on them. the 1st flash site i tried to open, gave me a popup sayin u need to install plugin(flashplayer) to view the site. i downloaded the plugin, and am running the installer, but wen i go bak into firefox, and look unnder plugins, the flash player isnt showing up..   A MORE SINISTER PROBLEM is everytime i open a flash website, or a site with any flash based ads, e.t.c, firefox just dies.. it just cuts out, and i'm not even getting that u need to download plugin..screen anymore.. i dunno whats going on,  but this is now a biig problem for me as most sites have flash in them, so  cant do anything..  HELLPP pleease..  am using edgy. and i think its the latest firefox version too (came with edgy)

I don't exactly understand that !!!  

When I did a trial install of Edgy, one of the things that worked properly (whereas it doesn't under Dapper) is the automatic installation of Flash Player.

Did you click on the little (I believe it is green) icon that pops up on the webpage that is wanting to use FLASH.  When I did and when I followed the FLASH installation prompts, it installed FLASH automatically, whereas in Dapper it will NOT install automatically and has to be done manually.

Anyway good luck.

---

### Post by adam.tropics on 2006-11-28
> **three-cushion said:**
> Hello:  I run Ubuntu on a Mac (Tiger 10.4.8) Don't think an i386 download will help me.. fact is, I get an ERROR  that it is not..
Have another URL for me to try?

Cheers, Jim B

Didn't realise you were on a mac. Well, unless you're on an Intel Mac,in which case I imagine (??) the standard one should work, you are (according to a forum search, I don't have a Mac) limited to Gnash. A thread [about it here]("http://www.ubuntuforums.org/showthread.php?t=199370&highlight=gnash") has a deb for ppc in post #7

---

### Post by lori.ann on 2006-11-28
> **AndyCooll said:**
> This is a known bug with FF and if you search on these forums you'll find a number of workrounds. What worked for me was to type into the command line the following:

```
sudo gedit /etc/X11/xorg.conf
```

I then found the "DefaultDepth" line and changed the setting to 24. I then restarted X (or it might be easier for you to restart your pc) and the problem was solved!

:cool:

I tried to install one of the alternatives but, while it seems to have installed fine, I suppose the other flash install is still on my system and that may explain why I still have a total firefox crash everytime I try to access flash. 

Do you know how I can uninstall what I installed? I just followed directions on a website the first time I tried to access a flash site, so I'm not really sure where it was installed or what it was called.

Also, can you tell me how to change the settings if I should follow your directions, quoted above? And how to "restart X"? I'm new to linux but think I follow step-by-step instructions pretty well :-) and I'm having fun learning.

Thanks!!

---

### Post by Zaen on 2006-11-28
I was thinking of updating to flashplayer8 soon, but from some of these posts it looks like this could be a bad idea? 

flashplayer7 works great, but too many places need at least flash player8 minimum. 

Is flash player 9 a better idea for an amd 32 bit cpu?

---

### Post by sonnywise on 2006-12-02
> **lori.ann said:**
> A great install HOW-to is available at [http://www.ubuntuforums.org/showthread.php?t=279990](http://www.ubuntuforums.org/showthread.php?t=279990).

This solved my problem with ubuntu 6.10 and firefox 2.0 crashing in many websites with flash plugins 8) 8) 8) 

Thank you so much.

---

### Post by CaveRat on 2006-12-02
> **sonnywise said:**
> This solved my problem with ubuntu 6.10 and firefox 2.0 crashing in many websites with flash plugins 8) 8) 8) 

Thank you so much.

Yes plus1 for this suggestion. The Flash 9 Beta seems to be working very nicely on my Buntu install.

---

