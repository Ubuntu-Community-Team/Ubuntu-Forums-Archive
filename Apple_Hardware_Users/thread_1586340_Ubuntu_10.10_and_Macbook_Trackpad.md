---
title: "Ubuntu 10.10 and Macbook Trackpad"
date: 2010-10-01
forum: Apple Hardware Users
---

### Post by mzruya on 2010-10-01
Hi, i recently upgraded to Ubuntu 10.10 RC 1, reinstalled all the packages necessary for the trackpad and still my (Macbook 5.5) trackpad almost stopped functioning completely.. i can only move the mouse pointer and click, no scrolling or two finger secondary click..

anyone managed to get a modern macbook pro trackpad to fully work on 10.10 like it does on 10.04 ?


Thanks !

---

### Post by Jekshadow on 2010-10-02
I have the exact same issue with my 6,2. It also appears that the settings dialog for trackpads has disappeared.

EDIT:

After installing uTouch, it detected the touchpad perfectly, and gesturetest successfully identified all of the gestures I threw at it (1-5 fingers, taps and swipes).

---

### Post by paulinchen on 2010-10-03
how did you get the utouch driver working? Does that mean you now have multitouch like in osx?

---

### Post by ichigo on 2010-10-05
i don't know how to get utouch running, but I could recover everything it could in 10.04 by installing
- xserver-xorg-input-synaptic
- bcm-5974-dkms from the maverick mactel repos.

Doing so, I get back the "Trackpad" tab under System->Preferences->Mouse

Nevertheless - as in 10.04 - this doesn't support three or four-finger gestures...

---

### Post by Jekshadow on 2010-10-05
> **paulinchen said:**
> how did you get the utouch driver working? Does that mean you now have multitouch like in osx?

uTouch didn't send any actions to the applications, so it doesn't actually do anything.

> **ichigo said:**
> i don't know how to get utouch running, but I could recover everything it could in 10.04 by installing
- xserver-xorg-input-synaptic
- bcm-5974-dkms from the maverick mactel repos.

Doing so, I get back the "Trackpad" tab under System->Preferences->Mouse

Nevertheless - as in 10.04 - this doesn't support three or four-finger gestures...

I tried that, it didn't work.

---

### Post by sharpone on 2010-10-07
I've got the latest RC of Ubuntu 10.10 running on my macbook pro 5,4. I'm interested to know if anyone figures out how to get the multitouch stuff working with it (uTouch?). Thanks.

---

### Post by kwiksand on 2010-10-07
I've got the same thing, install 10.10 new after being on 10.04 for a while using the multitouch drivers (in this forum).  Now Installed just with bcm5974 default and installed UTouch as well, but no multitouch thus far.

Of course two finger scrolling works.

Cheers

---

### Post by Nikos.Alexandris on 2010-10-20
> **ichigo said:**
> i don't know how to get utouch running, but I could recover everything it could in 10.04 by installing
- xserver-xorg-input-synaptic
- bcm-5974-dkms from the maverick mactel repos.

Doing so, I get back the "Trackpad" tab under System->Preferences->Mouse

Nevertheless - as in 10.04 - this doesn't support three or four-finger gestures...

After upgrading to 10.10, the "xserver-xorg-input-synaptic" package was missing (with the mactel ppa enabled and all other mac-relevant packages upgraded). Installed it manually and the trackpad works as before.

Thanks, Nikos

---

### Post by smoors on 2010-10-21
Hi!!

I'm experiencing the same problems. It really bugged me that the touchpad-speed was so dead slow. 
I could change it with "pointing devices" dialog, but this changed was reverted after every X-restart. 
Finally, i managed to get a workaround for this issue... You can set the properties of the bcm module by commandline with the tool "xinput".  
First of all, you can list the current settings with xinput list-props "bcm5974". After i played a little bit around with the "pointing devices"-dialog, i found some settings which pleased me. Then i executed the xinput list
command and used the values to set them via commandline. 
Here's an example which sets the speed (for a macbook pro 5.5), i put it in my .bashrc to execute it at every login:

[FONT=System]xinput set-prop "bcm5974" "Synaptics Move Speed" 0.711864, 5.050848, 0.102339, 0.000000






[/FONT]

---

### Post by smoors on 2010-10-21
Btw, does someone got right-clicking with the touchpad working? Besides that, i can't "drag and move", or whatever the action is called when you click and move the cursor, for example if one wants to select text.

---

### Post by vgrisham on 2010-10-21
This is the big problem for me on my Macbook Pro (5,3). I could give a rats backside about four fingered multitouch. I just want to be able to drag and drop stuff. 

I had this problem in Lucid too, but following [these]("https://help.ubuntu.com/community/MacBookPro5-3/Lucid#Touchpad") instructions, I was able to get the trackpad to be functional. Not so with Maverick. The bcm5974-dkms_1.1.4_all_test.deb workaround no longer seems to be cutting it.

---

### Post by smoors on 2010-10-21
> **vgrisham said:**
> 
I had this problem in Lucid too, but following [these]("https://help.ubuntu.com/community/MacBookPro5-3/Lucid#Touchpad") instructions, I was able to get the trackpad to be functional. Not so with Maverick. The bcm5974-dkms_1.1.4_all_test.deb workaround no longer seems to be cutting it.

Thanks for the hint, that got me a little bit further. At least the page stated that right-click is possible with a two-finger click. That was new to me.. 

Apart from that, i found out that you can drag at least a window by double-tapping on the top of the window(where the title is). 

Even with those hints the trackpad is hard to use.. i find it selecting text sometimes when it should not and those irritating things. I *really* would like to use linux more often on my macbook and the touchpad is one of the last things that doesn't work :(

---

### Post by kosumi68 on 2010-10-21
[http://ubuntuforums.org/showpost.php?p=10007145&postcount=280](http://ubuntuforums.org/showpost.php?p=10007145&postcount=280)

The amd64 version should be available in an hour or so...

---

### Post by micseydel on 2010-10-24
My MBP 5,5 had the touchpad stop working when I upgraded from 10.04 to 10.10. I installed utouch, without improvement, then xserver-xorg-input-synaptic then bcm5974 and the touchpad started working again (what a relief!). I haven't managed to get the multitouch working that I was hoping for though.

> **Jekshadow said:**
> After installing uTouch, it detected the touchpad perfectly, and gesturetest successfully identified all of the gestures I threw at it (1-5 fingers, taps and swipes).
How did you use gesturetest? I tried to use it on the terminal, but can't figure out what to use for the mask.

---

