---
title: "cannot enable desktop effects"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by poobalanc on 2008-03-20
hie all

good day.

im a beginner, just start to play around with the Linux.

i have install Ubuntu 7.10 gutsy. 64 bit. i couldn't enable desktop effects. Im using ATI radeon xpress 1100. 

what should i do? how to enable it? what is the requirement if i need to use compiz? or cube effects in my PC.

thanks.:confused:

---

### Post by aJayRoo on 2008-03-20
I'm not sure if the ati graphics driver works with compiz currently. I found the best option was to use the restricted drivers manager to install the driver for my ati card and then install the xgl xserver. It is very straight forward and no special configuration should be required, simply open up synaptic package manager, search for 'xserver-xgl' and install the package with that name. Alternatively using the command line you would type:
```
sudo apt-get install xserver-xgl
```
Once this is installed you should log out and back in again and the xgl xserver should be used automatically (if not try restarting the xserver). Xgl takes a little longer to load but should allow you to use desktop effects at a decent speed. If it doesn't work you can revert to the old xserver simply by removing the 'xserver-xgl' package. Xgl will not work well (or at all) if you use dual monitors though so if that is the case you will need to try something else. Hope that helps.

---

### Post by jonnywombat on 2008-03-20
Hi there...

Have you installed the restricted drivers for your graphics card???

You need to to use the 3d effects... If you search the forums for your card you will find instructions on how to install the correct drivers... If you draw a blank then search for "envy" also.


Jonny

---

### Post by poobalanc on 2008-03-20
ajay and ronny, 

thanks for your good advice. 
first of all, i dint enable the restricted driver.
and then, i did as how ajay suggest. seems it works. i could enable the desktop effects. about the compiz cube, im not sure. i have to try first. will let u know guys. 

thanks again.

you all are more kind than Microsoft people.!

---

### Post by aJayRoo on 2008-03-20
Oh I forgot to mention an important step in allowing you to configure desktop effects like the cube (I thought it best to see if you could actually get desktop effects running first!).
You should install the package ' compizconfig-settings-manager' either from synaptic or from the command line with:
```
sudo apt-get install compizconfig-settings-manager
```
This should give you an extra option in the desktop effects setting tab. The settings manager is also accessible through System->Preferences->Advanced Desktop Effects Settings. Using the settings manager you should be able to configure the cube etc.

---

### Post by iSplicer on 2008-03-20
I find that a little weird. Why not just simply include the settings manager by default??

---

### Post by aJayRoo on 2008-03-20
I'm not sure really. I guess it is because it can be used to alter pretty much anything that compiz does, and is too complex for beginners perhaps. I would have thought it better to include and have it labeled advanced settings or something but then again there is probably some good reason why that isn't the case... Just a guess!

---

### Post by CJ56 on 2008-03-20
If you want a good tutorial on getting the cube etc. to work, I find this one very useful -

[orlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion]("orlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion")

Hope it helps... ;)

Sorry - that should say -

[Forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion]("Forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion")

Oops...

---

### Post by BL00dFox on 2008-03-20
> **CJ56 said:**
> If you want a good tutorial on getting the cube etc. to work, I find this one very useful -

[orlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion]("orlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion")

Hope it helps... ;)

Thanks!

---

### Post by poobalanc on 2008-03-21
thank you guys. i made it.

---

