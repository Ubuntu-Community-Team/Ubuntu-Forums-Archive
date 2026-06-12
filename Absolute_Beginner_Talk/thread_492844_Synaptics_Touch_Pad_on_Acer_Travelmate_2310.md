---
title: "Synaptics Touch Pad on Acer Travelmate 2310"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by cool_penguin on 2007-07-05
Hi Guys,

Firstly i would like to thank the UBUNTU team and all you guys for making Ubuntu such a grand success. I recently switched over to Ubuntu after having a hard time with with windows and after being rather unhappy with Xandros. Ubuntu works great and i can feel the stability. I have one small issue though.

I have an Acer Travelmate 2310 series which comes with a Synaptics touchpad. I would like to activate functions like tap to click, tap to drag and drop, tap to scroll, etc. I was looking up various posts on this form and all point out to editing the Synaptics touchpad section in the xorg.conf file. However when i open the xorg.conf file, i just see Input device as "Configured Mouse". I read the entire file carefully and there is not a single word like Synaptics or touchpad. 

Even towards the end of the file (where everything in listed), i see configured mouse. 

When i check for Hardware information (Preferences --> Hardware Info), i see it been detected as Synaptics touch pad. 

Can anybody help me with this. I would like to configure my touchpad, but since i do not see any info regarding the same on the xorg.conf file, i am unable to do stuff and run applications like qsynaptics. 

Thanks a lot in advance. 

Keep up the great work guys.

Cheers,
Harry

---

### Post by slimdog360 on 2007-07-05
[>    1.   If you set MaxTapTime=0 in the X config file then the touchpad will not use tapping at all, i.e. touching/tapping will not be taken as a mouse click.
   2. If, instead, you set MaxTapMove=0 in the X config file, then the touchpad will not use tapping for a single finger tap (left mouse button click) but will for the two and three finger tap (middle and right button click).


hence try changing these values to something like 100 or something. There is more in the links.

taken from this site
[http://web.telia.com/~u89404340/touchpad/]("http://web.telia.com/~u89404340/touchpad/")

a bit more stuff here [http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad]("http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad")

before you go changing anything first put this into a terminal 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

if something goes wrong you get back to your current configuration by using this 
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

---

### Post by cool_penguin on 2007-07-05
Thanks a lot dude. Shall try it this evening and post back.

Cheers,
harry

---

