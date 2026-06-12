---
title: "Serious Screen Resolution problem..."
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by Linux_freek on 2008-04-11
Helllo All,

My cpu specs :
Ubuntu 7.10 amd64
ram - 1.5GB
Processor : dual core 3.0 Ghz 
MBd : Intel 945 GNT or D945GNT
Screen:Samsung SyncMaster 920nw
Problem. Cant switch to Widescreen resolution modes with the open source driver available :(...

1. When i go to Screens n resolution window.
and select following.
Screens: Lcd 1440x900 
Gdriver intel 945 
and when i set it and log out and log in back .
I get screen switched to 1024x768 mode :(

When i set screen from Screen resolution ...
then i have the screen shrinked to half of the width and inside it shows it has set to 1440x900 @56 hz (which is perfect ) but what about the screen size it shrinks to half the width ...


I have already tried all Syncmaster 930 and 910 in monters ... with Gdriver set to intel 945 .


Can any body please help ....  and if i have missed out something please explain ......


Thanks in advance Please help! :)

---

### Post by wolfen69 on 2008-04-11
try in terminal:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by kciuq on 2008-04-11
This worked for me, i use a Samsung SyncMaster 226BW
Go to
System>Screen and Graphics Preferences
Chose your screen model and mark the "Widescreen monitor" checkbox.
If you can find your model, it should bring up widescreen resolutions under the resolution menu.
If not, you'll have to edit your xorg.conf,

---

### Post by Linux_freek on 2008-04-11
i have done both of the things :) . after doing
 sudo dpkg-reconfigure xserver-xorg 
I restarted the comp and switched to 1440x900 @ 60 hz and 24bit color
what happened is my screen is 3 inch reduced in width a kind of shrinked 1 can say :P
I have already tried to correct it by moniter settings but cant correct it :( .... completely clueless about the reason. Can any one help me out cause its working absoultely fine (wiht all res. modes perfect) With Win XP ( i am not win promoter though :D) 

Also other modes like 1280x1024 @60hz works fine ... 

Also please tell me what to do after running the configuration of :
sudo dpkg-reconfigure xserver-xorg
as after doing it there is no effect ... nothing is set :(

---

