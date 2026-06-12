---
title: "PPC - G5 iMac Video Question"
date: 2008-04-23
forum: Apple Hardware Users
---

### Post by rectagonal on 2008-04-23
Im thinking of picking up an iMac G5 and putting Ubuntu on it, as the primary operating system.

I use Xubuntu on a Tangerine G3 iBook already and I am quite familiar with Linux on PPC hardware and the limitations there in and etc. But I am wondering which variation of the iMac G5 to get, specifically in reference to the video card.

I am pretty certain the nVidia model wont have 3d support, but was  curious how well the open source drivers covered the Radeon 9600 and or the Radeon X600 Pro in the later two models ?

---

### Post by stream303 on 2008-04-23
I'm running the early model 20" G5 iMac here (no light-sensor or camera) and it has a built-in nvidia card.

I'm glad you brought this up.  Currently there is a slight bug in the nv video driver on the 20" g5 iMac that shifts the screen to the right about a half-inch and wraps back around to the left.  This bug is coming from way upstream at freedesktop.org and has been verified and reported, so I am waiting for a fix.

It is slightly annoying, but with the large amount of screen real-estate, I can work around it.

Gutsy was the first version to show this problem, and my fix was to use the nv driver from Feisty.  For now I am just waiting for a fix to trickly back down through Debian and Ubuntu.

I'm not sure if this would be a problem on the smaller screens. For me, I can live with it, but it is slightly annoying.

Note that there are no brightness control capabilities either, although I find the default setting to be ok.  I fake it by using small amounts of xgamma compensation, or use Xubuntu, which has a very nice faux-brightness control.

Be sure to see this for some additional hardware specs to help make your decision:
[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

I think I have heard of success with the "B" model with the light-sensor, and am not sure of the last model with the isight camera..

Hopefully if you go with the ALS or Isight versions with their Radeons, you won't have too much trouble..

---

### Post by stream303 on 2008-04-23
Forgot about this:  be sure you can get your money back or can inspect the machine first.

Some of the G5 iMacs got caught in that wave of capacitor-failures that hit a lot of manufacturers.  Check for signs of overheating like yellowed plastic on the front panel in front of the power supply and see if the motherboard or ps has been replaced.  If you can physically inspect it, open the back and look for capacitor leakage, or "bulged" can-tops.

That being said, my iMac has been rock solid, and I've put it through hell and back with numerous installs with fans screaming, (which they will do with Ubuntu currently until after the first reboot).  No signs of cap-leakage on mine.  Just wanted to point out "buyer beware".

Btw, the screaming fan issue upon installation is being looked into by a dev, and is slated for a fix on the next spin, 8.04.1, but there is hope that maybe the actual release will have it - maybe.  At any rate, don't be freaked out during install - it calms down after the first reboot.

---

