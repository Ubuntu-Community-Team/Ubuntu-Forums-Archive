---
title: "A few newbie questions"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Gam3Junki3 on 2007-08-22
I installed feisty fawn and I'm dual booting with Windows Vista. Both are working perfectly (Well windows is). The highest resolution I can get is 1024x768 so I was wondering how I can get 1280x1024? And for the matter how I can ensure that my video card is fully functional as well as any other hardware that might not be working properly.

If there is some command or something to give you any information or something you need let me know.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-22
as far as you video card 
run 
glxgears


then for your  high res .... ummm give me a min

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-22
you have to edit your xorg.conf file but i dont rember what to do :(

---

### Post by ramjet_1953 on 2007-08-22
What is your video card / chipset?

To get the best resolution and to have 3D you will probably need to load a driver for your card.

Check out this link:[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Graphics_Card](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Graphics_Card)

Regards,
Roger :cool:

---

### Post by Gam3Junki3 on 2007-08-22
3508 frames in 5.0 seconds = 699.984 FPS
4200 frames in 5.1 seconds = 829.361 FPS
4200 frames in 5.1 seconds = 829.451 FPS
4200 frames in 5.1 seconds = 830.258 FPS
4200 frames in 5.1 seconds = 830.063 FPS
4200 frames in 5.1 seconds = 829.784 FPS
4200 frames in 5.1 seconds = 829.594 FPS
4197 frames in 5.1 seconds = 829.947 FPS
4200 frames in 5.1 seconds = 830.568 FPS
4200 frames in 5.1 seconds = 823.097 FPS
4320 frames in 5.1 seconds = 850.366 FPS
4320 frames in 5.0 seconds = 861.575 FPS
4320 frames in 5.0 seconds = 862.813 FPS
4320 frames in 5.0 seconds = 860.188 FPS
4320 frames in 5.1 seconds = 841.870 FPS
4297 frames in 5.0 seconds = 858.238 FPS
6000 frames in 5.1 seconds = 1178.346 FPS
6120 frames in 5.1 seconds = 1203.271 FPS
6120 frames in 5.0 seconds = 1220.437 FPS
6120 frames in 5.1 seconds = 1210.514 FPS


I assume it never ends, but this is what I got.

In the restricted device manager it said my hardware didn't need any restricted drivers.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-22
and the gears spin prity then it is working

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-22
ok i just found this online never did it my self so give it a try 
run that in the turminal

[PHP]sudo dpkg-reconfigure xserver-xorg[/PHP]

should walk you through some stuff lol hope it works

if you cripple your xorg.conf file your in bigg doggy poo so be carefull how should you be careful bets me

see if that will get you your res

---

### Post by Gam3Junki3 on 2007-08-22
I have nvidia 8600gt, it originally came with a 6100le integrated chipset/vid card.

I was told that the restricted drivers have better 3d capabilities. How do i get those? or is this true?

---

### Post by logos34 on 2007-08-22
> **Gam3Junki3 said:**
> I have nvidia 8600gt, it originally came with a 6100le integrated chipset/vid card.

You need to install the restricted drivers (despite what the manager says) if you want a better selection of resolutions.  Then run the x configuration tool and restart desktop:

sudo apt-get install nvidia-glx-new

sudo nvidia-glx-config enable

ctrl+alt+backspace


nvidia-settings

---

### Post by pgar23 on 2007-08-22
> **<<joe>> said:**
> ok i just found this online never did it my self so give it a try 
run that in the turminal

[php]sudo dpkg-reconfigure xserver-xorg[/php]should walk you through some stuff lol hope it works

if you cripple your xorg.conf file your in bigg doggy poo so be carefull how should you be careful bets me

see if that will get you your res

If you are new to using linux...you should probably not fiddle with the xorg.conf files unless u are positive you know what you are doing. and also...you said XP is working for you, but ubuntu isnt? if your having trouble dualbooting see my signature, has the easiest method of dual boot. (AND ITS A VIDEO TUTORIAL)

---

### Post by Gam3Junki3 on 2007-08-22
I'm not having trouble dual booting, Vista is working fine.

I'm having trouble with Ubuntu because I'm new. That's all i meant.
I've edited the xorg files before, and I won't learn if I don't try. --

edit:// I assume to get the restricted drivers I need the nvidia glx? 

I tried installing it but I got an error. "Error: Dependency is not satisfiable: nvidia-kernel-100.14.11"
So that's where I'm stuck.

---

