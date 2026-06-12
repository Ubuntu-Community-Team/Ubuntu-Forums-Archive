---
title: "more video problems with my nvidia fx5200"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Miroku on 2007-05-01
reposted from another thread because i think it needs its own  thread

so i am planning to use that envy program some1 suggested, hopefully it doesnt blow up the xserver whenever i tried to get the right drivers the first time.

so i tried gettin envy thru the terminal window but i got this error:

```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envy 
```

i went to the website and downloaded the proper .deb.


im greatful for the help in gettin rid of the lines, but i want to get the full potential out of my hardware if possible -- yes i am greedy like that =]

btw, i have a nvidia fx5200 that came with my dell. if anyone has a simpler way of installin the correct drivers, please let me know before i destroy my computer once again. thanks.

------------------update --------------

alrite, so i ran the envy program and told it to install the nvidia drivers. unfortunately, the xserver crashed again, just like it did the first time i tried to do something with the drivers.

i was able to reconfig and i logged back in, but now its tellin me there is a broken depedency. 

synaptic tells me it has to do with 'nvidia-glx-dev'

also after
```
glxinfo | grep direct 
```

i get this:

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```



what should i do with it now? complete removal or something else? and one other question that i should have asked a long time ago, how do i know that i have the correct version video drivers currently? -- i remember in windows, if it wasnt the correct version, it would show incompatibility. 

i want my video card backk just how i had it in windowss =...|

any help would be much appreciated.

---

### Post by Gazneth on 2007-05-01
Check your repository list and make sure your universe and multiverse are enabled. Envy shows up in my synaptic. Also the nvidia drivers as Non-free Linux 2.6.17 modules on 386. My repo list is pretty generic, so I'm pretty sure they are in universe or multiverse.

---

### Post by Nythain on 2007-05-01
are you running feisty, because a simple sudo apt-get install nvidia-glx-new nvidia-kernel-common would have probably done the trick... i forget the command to enable them, but all i think that command does is just change nv to nvidia in your xorg.conf... speaking of wich, have you been sure to do that

---

### Post by Miroku on 2007-05-01
i neglected to mention that yes, i am running 6.10 edgy that is fully updated.

> but all i think that command does is just change nv to nvidia in your xorg.conf... speaking of wich, have you been sure to do that

i am not realy sure about what you mean to change nv to nvidia in my xorg.conf

whenever my xserver crashed, i remember when i was reconfiguring it, i had to choose nV, as there was no nvidia.

> Check your repository list and make sure your universe and multiverse are enabled. Envy shows up in my synaptic. Also the nvidia drivers as Non-free Linux 2.6.17 modules on 386. My repo list is pretty generic, so I'm pretty sure they are in universe or multiverse.

i am pretty sure i enabled them a while ago, but i dont know hot to get back to those settings, is there any way i can check?

---

### Post by Miroku on 2007-05-03
so after the no replies, i went to get educated, and i tried several things.

i changed the driver to 'nvidia', which gave me xserver crash. so i went back to 'nv'.

i tried installin the normal way, got broken dependencies, which i fixed, and then restarted and xserver crashed.

i tried switching to the 'vesa' drivers, because i read somewhere that if you install the nvidia drivers through that, it may start working. using the vesa drivers got the monitor telling me that it did not support the resolution, so i went back to 'nv'.

then i used this:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy ](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy ) with method 1 using the internet. i installed this after uninstalling everything related to nvidia through synaptic as someone suggested here:

[http://ubuntuforums.org/showthread.php?t=221313](http://ubuntuforums.org/showthread.php?t=221313)

AND THEN, after ctrl + alt + backspace, it started working and everything seemed perfect! glx enabled and i could use the nvidia settings application. it was amazing, all of my programs were loading faster and all that good stuff.

then, i restarted my computer, and guess what? -- same xserver crash, but this time, the funny part was that when i switched to 'nv', it loads up till the login screen. after i login, the screen goes black, the monitor is telling me it doesnt support the resolution. and this is where i have stopped.

also, maybe if it has something to do with anything, using 'nvidia settings' i changed my resolution to my normal and i saved to 'xorg config' using the button in 'nvidia settings'. whenever i did it, everything seemed good and everything was working smoothly. one thing was whenever i ubuntu told me the refresh rate it said something like '89.9' or something but 'nvidia settings' told me 60 hz. idk if that has anything to do with it but man this is gettin discouraging. is it suppose to be this hard when linux supposedly has great relations with nvidia and especially an older card like my fx5200? 

very unhappy right now.

the only thing i can think of now is to go thru the last link i pasted in here and if that dont work, i have no idea. maybe i am not ready for linux. =(

---

### Post by Miroku on 2007-05-04
so i am back ... with more motivation because of the lack of replies -- makin me work harder. but here goes ...

so i uninstalled everything related to nvidia through synaptic, afterwards i did use method 2 from the guide also using the recommendations from problem #7. i used the latest drivers from the nvidia linux website. everything seems A OK. 

system --> preferences --> screen resolution still reports 50 hz

however, nvidia is telling me its 60 hz which is confirmed by the monitor itself telling me it is running in 60 hz, so i think the system is mistaken. will report any problems in the future, hopefully there wont be any.

thanks for the awesome guides tseliot

---

