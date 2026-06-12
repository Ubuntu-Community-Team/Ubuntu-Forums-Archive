---
title: "very confused with videocard driver installation (ati)"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by atd85 on 2007-03-23
i've been reading tons of posts about how to install ati drivers, but they all seem to be a little different.. can someone please explain to me to terms binary driver, firegl, etc.. i downloaded the drivers from ati's website for my mobility x1300, called "ati-driver-installer-8.34.8-x86.x86_64.run", double clicked it and went through the graphical installation and then i was able to set my resolution to the proper one (1280x800) but the ati control panel didnt work, so i downloaded fglrx-control and then it worked, although its not very useful, but i have this feeling, based on these other posts i've read that i'm still missing something in my installation because i dont think that 3d acceleration is working.. i try running glxgears and i get this error, "Xlib:  extension "XFree86-DRI" missing on display ":0.0"." but it still runs.. although it appears to be running very slowly.. fglrxinfo gives me this.. 

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

someone please help clear this all up, my 2d desktop works and looks fine, but it bugs me because i'm pretty sure its an incomplete or improperly configured installation, and i have no idea what any of these terms mean.. i'd like to have a better understanding of things for when i try to configure my ati card on my desktop (radeon 9800) for dual display, and in case i ever wanna run anything that requires 3d acceleration. thanks in advance

---

### Post by overdrank on 2007-03-23
> **atd85 said:**
> i've been reading tons of posts about how to install ati drivers, but they all seem to be a little different.. can someone please explain to me to terms binary driver, firegl, etc.. i downloaded the drivers from ati's website for my mobility x1300, called "ati-driver-installer-8.34.8-x86.x86_64.run", double clicked it and went through the graphical installation and then i was able to set my resolution to the proper one (1280x800) but the ati control panel didnt work, so i downloaded fglrx-control and then it worked, although its not very useful, but i have this feeling, based on these other posts i've read that i'm still missing something in my installation because i dont think that 3d acceleration is working.. i try running glxgears and i get this error, "Xlib:  extension "XFree86-DRI" missing on display ":0.0"." but it still runs.. although it appears to be running very slowly.. fglrxinfo gives me this.. 

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

someone please help clear this all up, my 2d desktop works and looks fine, but it bugs me because i'm pretty sure its an incomplete or improperly configured installation, and i have no idea what any of these terms mean.. i'd like to have a better understanding of things for when i try to configure my ati card on my desktop (radeon 9800) for dual display, and in case i ever wanna run anything that requires 3d acceleration. thanks in advance

Hi and welcome, I wish I could explain the drivers that you requested but I cant. I myself am still learning, what I can supply you with a link that work for me on the ati drivers
[http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/](http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/)
follow the instructions on the page and it will install the best drivers to get you going. Hope this helps! Good luck!

---

### Post by atd85 on 2007-03-24
i downloaded the package from the website and it says i need a whole bunch of dependencies.. maybe i'll give it a shot later when i have some more time (i'm on dialup).. has anyone else used this though?

also a bump for anyone who can clarify the terms.. thanks in advance

---

### Post by atd85 on 2007-03-25
bump

---

### Post by Campingman on 2007-03-25
I have an ati card, a bit older than yours and always follow this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
Always works for me
I had an issue with my ati driver reverting to mesa all the time (caused by messing about trying to get Beryl to work).  In the end I could not solve it and had to remove everything and start again!
Hop you have more luck.

---

### Post by Jim D v2.0 on 2007-03-25
> Hi and welcome, I wish I could explain the drivers that you requested but I cant. I myself am still learning, what I can supply you with a link that work for me on the ati drivers
[http://discoverx.wordpress.com/2007/...ers-in-ubuntu/](http://discoverx.wordpress.com/2007/...ers-in-ubuntu/)
follow the instructions on the page and it will install the best drivers to get you going. Hope this helps! Good luck!

I too was having all kinds of problems getting the ati drivers installed and working but this link solved all of my video problems. It takes a bit of time but seems to work quite well.

Thank you for posting this.

---

### Post by 67GTA on 2007-03-25
The only way I got mine to work was with Envy. It is a program created by Alberto Milone. It will intall the best driver and get your Direct rendering and 3D acceleration working. Might give it a try. Here is the link.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by cowlip on 2007-03-25
Envy seems to be popular these days: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Or a walkthrough, if you prefer: [http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

---

### Post by atd85 on 2007-03-26
thanks a lot for all the replies.. i didnt realize envy was so popular.. but i have one more quick question.. will it automatically replace my current driver installation? or will i have some kinda problem since i already did it a different way? should i remove my current driver first? thanks again.

---

### Post by lamalex on 2007-03-26
you shouldn't have a problem. I always say don't use envy. I've seen it break a lot of people's X servers. (X being the graphical component). It sounds like your driver install went fine and you don't need to do anything at all. The ATI control panel for linux is USELESS. nothing you do will fix that, except call ati over and over until they give us some support. Email your computer vendor and tell them you want them to request support from ATI for linux, also email/call/write ati yourself. Community is the only way we'll fix ati's shotty suppot. so yeah, you don't need to do anything if your resolution stuff was fixed. if you want, type this into a terminal and make sure fglrx shows up.
```
cat /etc/X11/xorg.conf |grep fglrx
```

also check the xorg.conf to make sure compositioning is disabled, that's a frequent cause of poor 3d

---

### Post by atd85 on 2007-03-26
when i typed that command it says Driver "fglrx" so i'm assuming its working right.. and i dont see anything about compositioning in my xorg.conf file.. but is there anyway i can test my 3d accel to make sure it is working right? cuz i was thinking about giving beryl a shot, but first i wanted to make sure my videocard was right so i didnt have any problems with it that would maybe cause beryl to not work right.. thanks again

---

### Post by lamalex on 2007-03-26
add this to the very end of your xorg.conf
```
Section "Extensions"
Option "Composite" "Disable"
EndSection

```
restart X and now type ```
glxinfo |grep direct
``` and if it says "direct rendering: yes" then you're good to go.

---

### Post by billybobjoe on 2007-03-27
Here is the error message I got when I tried to add what was in Iamaley's second to last post after I typed in glxinfo |grep direct.

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

I tried the first solution in campingmans link, but found the second solution in the link to work.  What am I missing?

Ive tried other "fixes" in other threads but they either dont work or cause Ubuntu not to load.

I have an ati x700 pro and a samsung syncmaster 940bw monitor.

---

### Post by atd85 on 2007-03-27
> **Iamalex said:**
> add this to the very end of your xorg.conf
```
Section "Extensions"
Option "Composite" "Disable"
EndSection

```
restart X and now type ```
glxinfo |grep direct
``` and if it says "direct rendering: yes" then you're good to go.

thanks a lot.. this seemed to work for me, i now get "direct rendering: yes" and glxgears runs smoothly now

---

