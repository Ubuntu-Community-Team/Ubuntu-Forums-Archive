---
title: "Macbook 3,1 trackpad"
date: 2010-05-18
forum: Apple Hardware Users
---

### Post by erictm on 2010-05-18
Since I have all the time in the world out here I've decided to give 10.4 a try after last using v8. So far so good, I was able to get my broadcom wireless working ([although it's very slow]("http://ubuntuforums.org/showthread.php?t=1487039")), but after spending some time searching through the forums and Google I have not quite found a good fix for the trackpad. Having an older Macbook, I don't have all the fancy features that come with the newer aluminum body Macbooks, so I didn't expect to have an issue. The trackpad is unresponsive, slow, and frustrating to the point that I have to plug in an external USB mouse. And although this fix works, it's not ideal.

Can somebody point me in the right direction for a fix, or perhaps a driver update for lynx and the trackpad? 

Oh and I'm sure this has been done to death, because I had the same issue on v8, so I appreciate the time and patience. 

Can't wait until I get a new laptop. :P

---

### Post by ditsch on 2010-05-18
You can install and use GSynaptics to tune the touchpad settings according to your needs.

---

### Post by erictm on 2010-05-19
Thanks.

 I installed it via the terminal using sudo apt-get. I'm not quite sure how to configure it though, or what settings users with a similar laptop are using. Not quite sure how to even bring it up to adjust the settings.

---

### Post by steve_d on 2010-05-19
> **erictm said:**
> Thanks.

 I installed it via the terminal using sudo apt-get. I'm not quite sure how to configure it though, or what settings users with a similar laptop are using. Not quite sure how to even bring it up to adjust the settings.

The gui side of it is under System -> Preferences -> Touchpad

I'm having some issues on a Macbook 4,1 with the touchpad as well. If I keep my finger flat on the touchpad I can move the cursor around without any issues. But if I use just my fingertip the touchpad doesn't respond at all. Even more frustrating is that if I do two finger scrolling I can use my fingertips and the page will scroll properly which tells me the driver can definitely detect my fingertip.

Have you tried planting your finger flat on the touchpad, and do you think that this may be why the cursor seems erratic for you if you go between finger flat and fingertip as you move the mouse cursor around?

Steve

EDIT:

If you follow [https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig](https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig) to enabled SHMConfig, you can then use synclient in a shell to fine tune your touchpad. I found the "FingherHigh" and "FingerLow" parameters needed to be dropped significantly to get a good response from the touchpad. Just note that your changes won't survive a reboot so take a look for how to make changes permanent if you find this helps. This link [http://wiki.archlinux.org/index.php/Touchpad_Synaptics#Configuration](http://wiki.archlinux.org/index.php/Touchpad_Synaptics#Configuration) may help although it lists the HAL fdi method as being depreciated... perhaps this has been flip flopping back and forth to xorg.conf and hal..?

---

