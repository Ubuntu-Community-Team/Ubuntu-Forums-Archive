---
title: "WINE &amp; WOW Performance - Extremely low fps"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by Fourdee on 2007-10-29
Hi all, 
installed Ubuntu last week, alot of things have changed since i last check out linux. I am a windows user, have been for about 10 years but since vista was a huge letdown, it was time for a change. 

Just have to say, seriously impressed with that linux/ubuntu has to offer and if i can just get World of warcraft to work, i will use it 90% of the time with dual boot XP.

**Anyway, not here to talk about windows.**

**My issue** 
(although not Ubuntu directly) is with WINE + games. 
I have managed to get WOW installed and running on wine , but with major issues. 
The framerate is around 5-30 compared to windows 150-300. 
Also its worth noting its really choppy, seems to be doing something wrong.
Also, when i run the game, its not full screen (window stretched) and when i leave the game my desktop resolution is 1600x instead of 1650 (little niggle i can live with).

 
**I currently have** :-

WINE (latest version, have tried a previous one also)
WOW installed
Nvidia 8800GTS (320mb)
core2duo 2.13ghz (@2.9)
2gb OCZ DDR 800mhz
Sata HDD's
X:FI (using onboard until creative, get, well, Creative? :) ) .
Comi Fuzion (cant remember exact name) - also tried with the "standard" setting for appearence, no difference.

**I have tried** :-
 directX /opengl, Regedit for the disable of Opengl Extensions listed on these forums.
Also tried setting config.wtf to opengl.
Tried OSA and ALSA in wine - also tried with it off
2 versions of WINE
2 nvidia drivers (GLX_NEW and ENVY latest)

None of the above makes any difference to FPS (be it 1% maybe, but not noticeable)

I have tried every idea that linux users have put up (google).

I have used windows for 10 years as i said earlier, been a Linux user before. I am lost for ideas. I understand it could be nvidia driver issues and/or the game itself, but i have read everywhere that people get "reasonable" framerates in Linux with WINE, mine are just too far off to reason with. 

Any ideas/suggestions, i would be greatful. 
Thanks in advanced
Apologies for the "other software" and not OS (unbuntu) related post.
Dan

---

### Post by Maestro23 on 2007-10-29
You probably already have, buy have you checked the Wine App DB for any suggestions?

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922)

---

### Post by sammael666 on 2007-10-29
two things come to my mind:

if you are using lowlatency/rt kernel you might give it a try with linux-image-generic kernel, according to this [https://answers.launchpad.net/ubuntu/+question/16498](https://answers.launchpad.net/ubuntu/+question/16498) lowlatency/rt kernels can cause poor wine performace.

second apply this regedit patch:
run regedit
   1.      Find this key HKEY_CURRENT_USER\Software\Wine\
   2.      Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder
   3.      Click right on the wine folder and select [NEW] then [KEY]
   4.      Replace the text New Key #1 with OpenGL
   5.      Click right in the right hand pane and select [NEW] then [String Value]
   6.      Replace New Value #1 with DisabledExtensions (Notice it's case sensitive!)
   7.      Then double click anywhere on the line, a dialog box will open.
   8.      In the value field type GL_ARB_vertex_buffer_object
(taken from [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft))

run wow in opengl mode (such as wine WoW.exe -opengl), for me personally the above patch doubled my fps.

hope it helps get you grinding mobs asap ;)

---

### Post by Crafty Kisses on 2007-10-29
> **Fourdee said:**
> Hi all, 
installed Ubuntu last week, alot of things have changed since i last check out linux. I am a windows user, have been for about 10 years but since vista was a huge letdown, it was time for a change. 

Just have to say, seriously impressed with that linux/ubuntu has to offer and if i can just get World of warcraft to work, i will use it 90% of the time with dual boot XP.

**Anyway, not here to talk about windows.**

**My issue** 
(although not Ubuntu directly) is with WINE + games. 
I have managed to get WOW installed and running on wine , but with major issues. 
The framerate is around 5-30 compared to windows 150-300. 
Also its worth noting its really choppy, seems to be doing something wrong.
Also, when i run the game, its not full screen (window stretched) and when i leave the game my desktop resolution is 1600x instead of 1650 (little niggle i can live with).

 
**I currently have** :-

WINE (latest version, have tried a previous one also)
WOW installed
Nvidia 8800GTS (320mb)
core2duo 2.13ghz (@2.9)
2gb OCZ DDR 800mhz
Sata HDD's
X:FI (using onboard until creative, get, well, Creative? :) ) .
Comi Fuzion (cant remember exact name) - also tried with the "standard" setting for appearence, no difference.

**I have tried** :-
 directX /opengl, Regedit for the disable of Opengl Extensions listed on these forums.
Also tried setting config.wtf to opengl.
Tried OSA and ALSA in wine - also tried with it off
2 versions of WINE
2 nvidia drivers (GLX_NEW and ENVY latest)

None of the above makes any difference to FPS (be it 1% maybe, but not noticeable)

I have tried every idea that linux users have put up (google).

I have used windows for 10 years as i said earlier, been a Linux user before. I am lost for ideas. I understand it could be nvidia driver issues and/or the game itself, but i have read everywhere that people get "reasonable" framerates in Linux with WINE, mine are just too far off to reason with. 

Any ideas/suggestions, i would be greatful. 
Thanks in advanced
Apologies for the "other software" and not OS (unbuntu) related post.
Dan
Do you have effects while this is going?

---

### Post by Fourdee on 2007-10-30
Thanks for the replies.

I will try linux-image-generic kernel tonight when i get home. Sounds promising.

I allready have wow in opengl mode with the config edit, also the regedit for disabled opengl extensions that you listed is all done. 

As for the effects (i assume you mean compiz fusion?) I have also tried with this on and off (standard appearance setting). No changes to framerates (be it 1% on average).

---

### Post by Fourdee on 2007-10-31
Ok i have tried the the open gl fix again, reinstalled wine and reconfigured it again.

My setup allready comes with the linux-image-generic kernel, so no changes there.

I cant seem to suss this one out, it feels like the game is running at 10% of total speed and more choppy than Vista running idle (compared to XP). Maybe its just the nvidia 8800gts card and driver setup or possibily the game itself. I cant for the life of me figure out how to improve my FPS.

So until either blizzard release a Linux client (i wish) or a possible new WINE/nvidia driver version fixes the issue, iam lost.

Until then, I will stick with XP for games, not what i would like to happen, but iam fussy about gameplay/framerates. I just hope one day i can play WOW on a linux/ubuntu setup as its literally the best Operating system i have ever used.

Thanks to everyone for their suggestions, much appreciated

---

### Post by dood123 on 2007-11-07
I am pretty new ubuntu user and I'd like to play WoW under ubuntu cause i got tired for windows. I have checked all kind of instructions to get WoW working. It works well altought with EXTREMELY low FPS its like 0.2

My comps specs are:
Intel celeron 2,4GHz
Ati radeon 9600 pro
512 RAM and thats all what i can say

And I have:
Ubuntu 7.10
Wine 0.9.48
WoW installed

I think the problem is in graphic drivers cause even screensavers are laggy, what should i do?

I really want this to work so please help.

---

### Post by sammael666 on 2007-11-07
in console type

glxinfo | grep rendering

it should say:
direct rendering: Yes

if it doesn't say so you need to reinstall your drivers. as much as i like to help u with that i can't as i am using nvidia graphic card and i don't know the procedure to install ati 3d drivers. try searching forums for ati driver howto or something similar.

---

