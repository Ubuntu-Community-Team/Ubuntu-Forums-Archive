---
title: "ATI binary X.org Driver Mobility Radeon X1800"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by dgoodma on 2007-12-12
Using Add/Remove I found the driver that matches what is on my HP laptop, ATI binary X.org Driver Mobility Radeon X1800. I installed. I do not see it in the Driver list under Screen and Graphics. How do I get it there, or how to I use it? Trying to take advantage of the additional desktop effects. And, after I "played" with the drivers, and set it back to what was default, every time I boot, it complains that the resolution cannot be determined, I hit continue and all is well; that message was not there b/4 I started trying to find where the install put the new driver. I also have Proprietary Drivers that were there when I set things up, but that one seemed to lock things up.

---

### Post by flamelab on 2007-12-12
Uninstall EVERYTHING regarding your ATI card (those things you installed I mean )
and then :

1) If you want the repositories ATI driver :

System --> Administration --> Restricted Drivers Manager

and choose your Graphics Card .
It will download the driver and install it on its own .
Then reboot or restart X (ctrl + alt +backspace ) and you have finished 
After that though you need to install these 

```
sudo apt-get install xserver-xgl compizconfig-settings-manager
```

and after restarting X you have AND Fusion :lolflag:

2) If you want the latest driver go here [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")
or download [envy]("http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu1_all.deb") that will do everything automatically .
If you install that driver you don't need XGL but you can activate Compiz whenever you want . But that driver is slower enough .

P.S. Install programs only from **Synaptic **!

---

### Post by dgoodma on 2007-12-12
Thanks, but that left me with strange results, could only go to 640 X 480 resolution... so; reverted back. 

Giving up for now.

---

### Post by flamelab on 2007-12-12
> **dgoodma said:**
> Thanks, but that left me with strange results, could only go to 640 X 480 resolution... so; reverted back. 

Giving up for now.

You'd better follow the instruction number 1 that is much simplier .
But you have first to remove all the ATI drivers you have installed and then install the proper one ;)

---

### Post by dgoodma on 2007-12-12
When I go with #1, it ends up with only 640 X 480 as the highest resolution. But when I revert back to what it does by default it works with higher res, and only complains about not knowing what is going on at boot time. So, for my laptop; I guess this process does not work, or I do not know what I am doing, either are possible.


Thanks for trying

---

