---
title: "geforce drivers"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by ~&#730;JaZ&#730;~ on 2007-06-08
Hi!
I have just bought a new graphic card (geforce 8600 gts), and i think that  the regular drivers that come with ubuntu arent good, I herd that there are 3 different drivers, for geforce graphic cards...so if anyone can help me how to change the drivers...i would appreciate it...btw the problems that i am having are that i have 5mm black edges on my monitor when i am using 1680x1050 resolution...

tnx for any help....
z

---

### Post by ayenack on 2007-06-08
**DON'T DO THIS IF YOU ARE NOT SURE**

Funny you should bring this up, you're correct the drivers that come with Ubuntu will not work. Nvidia has not yet released drivers for this card on any GNU Linux platform. As far as I know you have to follow these [instructions]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beta_Graphics_Driver_.28NVIDIA.29") to install the beta drivers. Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=453942") for pitfalls and possible solutions. Strongly recommend removing linux-restricted-modules and any Nvidia drivers you have installed before you try to install the BETA drivers. All the instructions on how to do this are on the above mentioned [thread]("http://ubuntuforums.org/showthread.php?p=2716324#post2716324"), you need to read all the posts carefully to get a full understanding of what might work.


Before you do this backup your xorg.conf. To do this type these commands in terminal.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

If anything goes wrong you can restore your original setup with these commands.

rm /etc/X11/xorg.conf
cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

Best of luck. ayenack.

PS. There are three drivers, nvidia-glx-legacy, nvidia-glx & nvidia-glx-new also some nvidia-glx-dev that you don't want to mess with.

---

