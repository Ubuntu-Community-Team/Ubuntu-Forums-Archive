---
title: "sound card is not recognised... creative sb x-fi 9000"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by BlueSilverMageDragon on 2008-03-07
i have the sb x-fi 9000 card in my computer... windows uses it just fine but ubuntu doesn't even show it exists... what do i need to do to get it working?  i am new to ubuntu and new to linux coming from windows xp and having a dual system while i try to leave windows behind.  i haven't even learned how to download cd's onto the computer using ubuntu.  i am new and braindead at the moment it seems. i know i can learn this but i am having trouble being pointed in the right direction when surfing the web in search of answers.

---

### Post by Crafty Kisses on 2008-03-07
For the CD burning, download k3b.
```
sudo apt-get install k3b
```
As goes your sound card, post the following output:
```
lspci
```

---

### Post by kpkeerthi on 2008-03-07
x-fi support for 32 bit is not fully available for linux yet. Some basic support, however, is available for 64-bit linux. Try searching in tutorials and tips section.. there is a HOW-TO for 64-bit gutsy. 

For more information see [http://opensource.creative.com/soundcard.html](http://opensource.creative.com/soundcard.html). Some users have reported to get it working in gutsy by compiling from latest alsa source.

---

### Post by BlueSilverMageDragon on 2008-03-07
this is what is said to me...
steve@steve-desktop:~$ sudo apt-get install k3b
Reading package lists... Done
Building dependency tree       
Reading state information... Done
k3b is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up timidity (2.13.2-15ubuntu1) ...
 * Starting timidity                                                                         * Starting TiMidity++ ALSA midi emulation...                                               ALSA lib confmisc.c:769:(parse_card) cannot find card ''
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
                                                                                     [fail]
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of songwrite:
 songwrite depends on timidity | playmidi | pmidi; however:
  Package timidity is not configured yet.
  Package playmidi is not installed.
  Package pmidi is not installed.
dpkg: error processing songwrite (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 timidity
 songwrite
E: Sub-process /usr/bin/dpkg returned an error code (1)
steve@steve-desktop:~$ 


apparently i did something else that didn't get finished and i am not learned enough to even come close to knowing what that all said... but i can figure out some... but NOT what to do to fix it... lol

---

### Post by BlueSilverMageDragon on 2008-03-07
i am not sure what i am doing wrong because it says "Setup is unable to detect a supported product on your system. please ensure that your product is properly installed before running the Setup program."  i have done that and like i said in a previous post... it runs on my windows xp without having to readjust it or anything.  do i get to cry now or can someone help me from the distance of the internet?

---

