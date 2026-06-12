---
title: "Problems with envy"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-10-16
After I installed envy and let it run, it prompted me to restart, which I did.  When ubuntu started it restricted the driver, so I un restricted it.  The problem is, I still can't increase my resoluton.  It's like nothing has changed, did I do something wrong?

---

### Post by LowSky on 2007-10-16
is it a Nvidia card

go into terminal and type 

sudo nvidia-settings

---

### Post by jpittack on 2007-10-16
Are you saying that when started Ubuntu, that you got a message that a restricted driver was in use?

---

### Post by techno-mole on 2007-10-16
what graphics card are you using ?
i used to use envy, but now i just run this in terminal 
```
 sudo aptitude nvidia-glx-new
```
after that it prompts about restricted drivers and such, then i run ```
 sudo nvidia-settings
``` in terminal and it lets you sort out resolutions and such.
but i couldnt tell you what you need to do regarding ati cards, so if you have an nvidia card remove envy and try running the codes i suggested, once you have set your resolution in the nvidia settings it gives the option to save the configuration, if you save it, it should use it everytime you start your system.
cheers

---

### Post by Dapman01 on 2007-10-16
> **techno-mole said:**
> what graphics card are you using ?
i used to use envy, but now i just run this in terminal 
```
 sudo aptitude nvidia-glx-new
```
after that it prompts about restricted drivers and such, then i run ```
 sudo nvidia-settings
``` in terminal and it lets you sort out resolutions and such.
but i couldnt tell you what you need to do regarding ati cards, so if you have an nvidia card remove envy and try running the codes i suggested, once you have set your resolution in the nvidia settings it gives the option to save the configuration, if you save it, it should use it everytime you start your system.
cheers

8800 GTS

---

### Post by techno-mole on 2007-10-16
you should be okay to use the codes i posted then (after removing envy) i use a 7600gs at the moment and thats all i need to do to set it up, and i havent had any problems.
cheers

---

