---
title: "Trackpad functionality with Macbook Pro 5.1"
date: 2009-01-17
forum: Apple Hardware Users
---

### Post by npfthunfan on 2009-01-17
I have just dual booted Ubuntu 8.10 on my Macbook Pro 5.1 (Late 2008). I am trying to get my trackpad to work... I currently can only move the mouse and left-click. I cannot tap, scroll, or right-click (normally two-finger tap). I tried getting gsynaptics but I don't know how to enable SHMconfig...

Anyone help me with the method i'm using or give me a better one?

---

### Post by ercoppa on 2009-01-17
Hi, read [this]("https://help.ubuntu.com/community/MacBook%20Aluminum#Trackpad").

Greets, ercoppa.

---

### Post by npfthunfan on 2009-01-17
Thanks... as you can tell I'm new to this

---

### Post by npfthunfan on 2009-01-17
I tried the stuff on that page, there was no change to the way my trackpad is acting... two finger scroll (which is set to 1) doesn't work... neither does anything other than left click

---

### Post by cyberdork33 on 2009-01-17
> **npfthunfan said:**
> I tried the stuff on that page, there was no change to the way my trackpad is acting... two finger scroll (which is set to 1) doesn't work... neither does anything other than left click
make sure you read the rest of the page:
[https://help.ubuntu.com/community/MacBook5-1/Intrepid](https://help.ubuntu.com/community/MacBook5-1/Intrepid)

Add the mactel repo and check the thread referenced there. 

Also, make sure that there is no configuration for the trackpad in your xorg.conf

---

### Post by npfthunfan on 2009-01-18
Ok, i'll take a look, how do I get to xorg.conf, I've seen loads about it but nothing to teach a beginner like me

---

### Post by Wisp558 on 2009-01-18
go to /etc/X11/xorg.conf.

A full command would be...

```
gksu gedit /etc/X11/xorg.conf
```

(Don't forget that the "X" in X11 is capitalized...)

---

### Post by npfthunfan on 2009-01-18
yeah... got that... still not getting any change in the behaviour of the trackpad... has anyone actually got it working on a Macbook Pro 5.1 (Aluminium)

---

### Post by npfthunfan on 2009-01-18
Ok finally got it working... I think I need to learn some patience and read every single word on the page... on cyberdork' link I only downloaded the packages mentioned rather than checking for others... the link is there somewhere on the page

---

### Post by andrei_elkin on 2009-07-24
According to symptoms mine has been the same issue: no right click nor vertical scrolling.
I am having 8.10 ubuntu on macbook pro 5.1.
However, 5.1 pro links were not helping until [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/337935](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/337935) was located.

---

### Post by eldamin on 2009-07-24
Hi,

I want share this valuable information that the touchpad for MacBook 5.1 is not supported completely in Jaunty (Ubuntu 9.04) as of Alpha 5 release. The pointer can move, and a physical left-click works, but that's it. I can not get tapping to respond as I could using the Mactel PPA packages with Intrepid (Ubuntu 8.10). I added the attached FDI policy file for the touchpad, and manually added the module bcm5974 to my /etc/modules file, however, Xorg is not loading or is not recognizing the touchpad policies. This file worked on Intrepid. The custom bcm5974-dkms package from the Mactel PPA provided support in Intrepid.

---

### Post by Dunkintori on 2009-11-27
My trackpad used to work perfectly with 8.10 and 9.04, but once I upgraded to 9.10 I cannot scroll anymore. The funny part is, right click still works!

I have a macbook 5.1, and I have done everything on this page(i did not really have to change much though because the instructions were almost literally the same for 9.04):
[https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic)

I'm officially giving up on logic and reason now, so does anyone have any crazy random ideas that I could try to make my trackpad scroll?

---

