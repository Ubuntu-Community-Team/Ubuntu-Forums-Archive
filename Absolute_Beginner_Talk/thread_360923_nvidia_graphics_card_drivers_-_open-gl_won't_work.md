---
title: "nvidia graphics card drivers - open-gl won't work"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by moredhel on 2007-02-13
I am unable to successfully run open-gl programs using xubuntu 6.10. I had it working last time (i wiped & started again).

I have tried using:

easyubuntu - it says might be illegal in some countries, i click ok and it does nothing.

envy - seems to install and 'glxgears' is fine, but games (eg frozenbubble & chromium) don't run at all.

envy beta - same as above.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29) - again, runs glxgears fine but not the games.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beta_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beta_Graphics_Driver_.28NVIDIA.29) - same again

in the past without the drivers games haven't run, then run fine once the drivers are installed, this time, the drivers are installed and nothing happens.

any help would be appreciated

thanks in advance :)

---

### Post by moredhel on 2007-02-13
it is note-worthy that before when i had the beta drivers (via the ubuntuguide way), it showed the non-beta splash screen when x server was started. Now it shows a much more plain one with beta driver written on it.

---

### Post by tronica on 2007-02-13
which card do you have? and could you post your Xorg log

open the terminal and type

> cat /var/log/Xorg.0.log

---

### Post by kelbizzle on 2007-02-13
[Envy]("http://albertomilone.com/nvidia_scripts1.html")  a python Script which installs and sets up the driver for you. I have used it 3 times today with 3 different nvidia cards. Directly after using Automatix to install all my software.

---

### Post by moredhel on 2007-02-14
If you read my post then you would of seen i have already tried envy & envy beta.

---

### Post by moredhel on 2007-02-14
@tronica: geforce fx 5200 (not a great card, but it is still good enough to not use legacy drivers)

my xorg log is rather long:

[http://www.collateraldesign.co.uk/xorglog.txt](http://www.collateraldesign.co.uk/xorglog.txt)

---

### Post by lalada on 2007-02-14
I have this problem too...

---

### Post by tronica on 2007-02-14
i have the same exact card as you, and works perfect.  can you post your xorg.conf. maybe theres something your missing in there,

---

### Post by MCSE_Crossover on 2007-02-14
Check /etc/X11/xorg.conf and make sure the driver line under your video card says "nvidia" and not "nv"

---

### Post by moredhel on 2007-02-15
very wierd - the next day it is fixed!

yay ^^

---

