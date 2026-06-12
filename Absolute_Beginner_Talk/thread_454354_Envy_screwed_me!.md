---
title: "Envy screwed me!"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by azizzle on 2007-05-25
Well, not really. But after I ran it and had it reconfigure my xorg i restarted to a blue screen. 
Problem;
Nvidia kernel module has the version 1.0-9755, but this X module has the version 1.0-9631

Now my question is why did this happen? Did I use the wrong version of Envy? I'm trying to set up my Nvidia 7900. Should I just go in and fix the version number manually? TIA

---

### Post by azizzle on 2007-05-25
anybody have any suggestions?

---

### Post by Hobo Joe on 2007-05-25
Try un-installing a re-installing through Envy and see if it works.

---

### Post by Terl on 2007-05-25
> **azizzle said:**
> anybody have any suggestions?

I would uninstall using envy.  Then, I would open synaptic and install nvidia-glx from there.  Edit xorg.cong hit ctrl-alt-bksp and you are done.

---

### Post by DoorGunner on 2007-05-25
Hi

I am unsure of envy. I used the regular nvidia drivers for my GE Force 6800 and it worked fine. 

One thing i can suggest is that you could reboot your computer and use the recovery mode. This will allow you to work in command line. What i would do is remove your envy driver and load the regular nvidia package. The instructions are found here.

[http://ubuntuguide.org/wiki/Ubuntu_Feisty](http://ubuntuguide.org/wiki/Ubuntu_Feisty)

I am going to be unavailable right now. but maybe this is a starting place for you.

---

