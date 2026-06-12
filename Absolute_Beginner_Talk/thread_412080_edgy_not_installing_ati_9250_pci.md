---
title: "edgy not installing ati 9250 pci"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by klein de usa on 2007-04-17
hi
`i have an old dell gx200, i have installed an (sapphre) ati 9250 pci card,  with a fresh install of edgy , my problem is that after the install when the xorg.conf file takes over in the start up i get a blank screen the blank screen comes right after the ubuntu loading screen and the login screen, i checked my xorg.conf and it is picking up my on board video card (NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]) 

how can i get edgy to use my ati 9250 pci card and not the on board video ? can i change the xorg.conf? 

i have the bios set to auto, settings are either auto or on board.
michine works fine with the new  ati 9250 pci card in:
win98se spaire hdd set up 
dsl linux live cd
puppy linux live cd

---

### Post by NicoleM on 2007-04-17
hi there

i had the same problem with that card and onboard video.

short answer: find the pci bus ID of your ati card and edit the xorg.conf file to use "ati" driver and that bus ID

long answer (with descriptions on how i did the above): [http://ubuntuforums.org/showpost.php?p=2353434&postcount=18](http://ubuntuforums.org/showpost.php?p=2353434&postcount=18)

when i ran into the issue i was brand new to linux (and still am!) but if you need any more clarification just post back and I'll do my best to try to explain what i did.

---

### Post by klein de usa on 2007-04-17
hi
ok 
that got me a little further along, i found my pci address and changed that and my driver to ati in the xorg.conf file , when i reconfigured , it told me no ati module found.
next i found a post that told me how to set my xorg.conf file to :
identifier  "Generic Video Card"
driver   "vesa"
 so i rebooted and now i'm looking at the ubuntu desk top wondering how i'm going to switch drivers from vesa to ati ??????????????? how can i do this ? if i use envy will it work or does it use the xorg.conf file as a guide ?

---

### Post by NicoleM on 2007-04-17
I'm no authority on the issue, but as long as you back up your working xorg.conf file I can't imagine trying envy would hurt.

when i ran envy it overwrote parts of the xorg.conf (or possibly even generated a new one?...not sure) so my guess is that it does the detection on its own.

i wish i could help more.  good luck though.

---

