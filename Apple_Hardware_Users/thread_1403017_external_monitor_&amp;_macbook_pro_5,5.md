---
title: "external monitor &amp; macbook pro 5,5"
date: 2010-02-09
forum: Apple Hardware Users
---

### Post by Grayer on 2010-02-09
Hi,

I have Kubuntu installed in my mac and I'm trying to connect the external monitor to it...it's a macbook pro 5,5.  It works fine with mac OS using midi display port to hdmi and hdmi-hdmi cable.  However, in kubuntu no matter what resolution i chose or whatever I do, the only thing that I manage to see is a zoom in of the desktop...its not blurry or anything so I don't think it's the graphic card.  Anyone have this problem?
Thanks.

---

### Post by linuxopjemac on 2010-02-10
what nvidia driver do you use ?
[http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=35](http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=35)

---

### Post by Grayer on 2010-02-10
Hi,
Thanks for replying.

I'm using the nvidia 185 driver, I'll update to the 190 and see what happens.  But I still believe that it's not a problem of the driver because I can see the screen, the only thing is that a part always gets cut off because the macbook resolution is much smaller than the tv.  Maybe it's because I don't know how to configure the external monitor.  How is it supposed to me done?

---

### Post by dennis123123 on 2010-02-10
Run ```
nvidia-settings
``` and follow the GUI as you would in Windows etc.

---

### Post by linuxopjemac on 2010-02-10
> nvidia-settings

This will bring up the settings manager
once you have things where you want them, go to the 2nd entry - X Server Display Configuration
Then click "Save to X Configuration File"

When I restarted, it saved my settings this time. Previously it would give me an error about 'no xconfig file' or something. Running nvidia-xconfig fixed that part.

[http://forums.nvidia.com/index.php?showtopic=150219](http://forums.nvidia.com/index.php?showtopic=150219)

---

### Post by buntuLo on 2010-02-10
> **Grayer said:**
> I'm using the nvidia 185 driver, I'll update to the 190 and see what happens.  But I still believe that it's not a problem of the driver because I can see the screen, the only thing is that a part always gets cut off because the macbook resolution is much smaller than the tv.
i quote from the nvidia 190.53 release notes:
*Fixed a problem that caused resolution limitations or corruption on certain DisplayPort devices such as the Apple 24" Cinema display or some DisplayPort to VGA adapters.*
nvidia 190.42 also corrected some other troubles with the display port.
i have your same problem with a few external beamers. i just downloaded 190.53 from the nvidia site, and installed it following [howto]("http://ubuntuforums.org/showthread.php?t=990978").
going to try it again tomorrow and report here.
ciao, Lo.

---

### Post by Grayer on 2010-02-10
Hi, I managed to install the nvidia 190 drivers but I'm still getting the same problems...I have attached a picture of what the thing looks like, who am I supposed to configure this?

---

### Post by linuxopjemac on 2010-02-10
[https://help.ubuntu.com/community/NvidiaMultiMonitors](https://help.ubuntu.com/community/NvidiaMultiMonitors)

---

### Post by Grayer on 2010-02-10
I'm doing exactly what it says in the link and still not workin :(. 
Could the problem be the way I connected the mac to the tv? mini dp to hdmi and hdmi to hdmi?
Thanks.

---

### Post by linuxopjemac on 2010-02-10
you have the 190.53 driver?

[http://mac.linux.be/content/nvidia-driver-19053-released-fix-apple-24-display](http://mac.linux.be/content/nvidia-driver-19053-released-fix-apple-24-display)

I guess when you have that driver in combination with a displayport-VGA cable, that it should work.

[http://store.apple.com/us/product/MB572Z/A](http://store.apple.com/us/product/MB572Z/A)

---

### Post by Grayer on 2010-02-10
Thanks, I'll try to purchase the cable and see how it works :)

---

### Post by buntuLo on 2010-02-11
it works for me with two external displays and one beamer, when connected with the MiniDisplayPort>VGA adapter and one VGA cable.

instead EDID informations are not retrieved from the device when a swith-box is in between the VGA cable (like in almost every lecture room equipped with a beamer). in this case the resolution drops to 640x480, and i still didn't find the correct way to force a higher resolution in the xorg.conf file.

---

### Post by Grayer on 2010-02-14
So I finally managed to fix this issue...just had to change the ratio of the tv screen to something else.  It's working fine for the most part but I'm getting a problem with graphical effects.  When I try to apply any graphical effect, such as explding windows when closing, the screen just turns grey.  Could this be a graphic card problem 

I'm using the twin view option if that helps...
Thanks.

---

