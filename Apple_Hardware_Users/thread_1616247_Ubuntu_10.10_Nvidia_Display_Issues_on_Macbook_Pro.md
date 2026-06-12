---
title: "Ubuntu 10.10 Nvidia Display Issues on Macbook Pro"
date: 2010-11-08
forum: Apple Hardware Users
---

### Post by Crell Moset on 2010-11-08
Greetings Citizens of Ubuntu Forums,

I just installed Ubuntu 10.10 on my Macbook Pro and so far everything is working perfectly except for my dual monitor configuration. Oddly enough, when running Ubuntu from the Live CD the dual monitors worked fine. It wasn't until after the installation and Ubuntu requesting I update my drivers that the problem arose. My GFX card is an Nvidia GeForce 8600M GT.

The issues are as follows:

1. Upon enabling the "NVIDIA accelerated graphics driver (version 173)" the Visual Effects worked however my dual monitors ceased to display anything. I noticed that monitor settings are now controlled by NVIDIA X Server Settings but nothing there seemed to fix the problem. When I try and apply the new settings I get the following error message: 

Cannot Apply
The current settings cannot be completely applied due to one or more of the following reasons: (then it lists a bunch of items which don't really apply to my situation.)

2. Some of the items on my menu bar seem to be pushed to the left when dual monitors are active.

3. Things seem to render choppy.

I tried disabling the Nvidia drivers and then my dual monitors worked again but now I can't get the Visual Effects to work.

Any assistance would be most appreciated.
Crell Moset

---

### Post by P4man on 2010-11-08
Dont use 173 drivers with that card, use the nvidia-current (185, and the recommended one for your card).

---

### Post by Crell Moset on 2010-11-08
I just tried enabling that driver and notice an improvement in performance however my second monitor still won't work. When I go to the NVIDIA X Server Settings and configure it as a Seperate X screen and press apply, I get the following error.

[IMG]http://i52.tinypic.com/3523x1g.png[/IMG]

After clicking on Apply What is Possible, nothing happens.


EDIT: This is strange... after simply rebooting my computer the Visual Effects stopped working. When I attempt to enable them I get the following error:

Desktop effects could not be enabled.

---

### Post by P4man on 2010-11-08
Try deleting your xorg.conf and make a new one with nvidia x settings. Or just make a new one with nvidia x settings and when it asks to merge, say NO.  I dont know by heart where that option is in x settings but you should be able to find it I think

---

