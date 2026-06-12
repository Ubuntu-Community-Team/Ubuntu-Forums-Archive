---
title: "Legacy Nvidia driver"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2008-03-27
I have installed the "Legacy Nvidia Driver" from Synaptic BUT I don't see that anything as far as my video setup has changed.

What do I have to do to apply this video driver ?

Is it a matter of manually editing the xorg.conf file ?  And, if so, is it a matter of replacing the video card driver parameter in the video card descriptor section of xorg.conf ?

And then the question becomes what is the "video descriptor" to use for this parameter ?

Thanks.

---

### Post by LowSky on 2008-03-27
go to system>admin>restricted drivers.

click the nvidia driver on

---

### Post by opscure on 2008-03-27
this page might help you:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by wpshooter on 2008-03-27
> **LowSky said:**
> go to system>admin>restricted drivers.

click the nvidia driver on

When I do that, what I wind up with is video resolution limited to a maximum of 800 x 600, whereas before I did that, I had a default Gutsy installation resolution of 1280 x 1024.

Thanks.

---

### Post by Malta paul on 2008-03-27
If I were you, I would use ENVY [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
Using Envy to disable your existing driver, reboot then again use envy to install the latest driver for your graphic card. After this go to System>Administration>Restricted Drivers Manager and tick 'Enable'  
Have fun :)

---

### Post by wpshooter on 2008-03-27
> **Malta paul said:**
> If I were you, I would use ENVY [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
Using Envy to disable your existing driver, reboot then again use envy to install the latest driver for your graphic card. After this go to System>Administration>Restricted Drivers Manager and tick 'Enable'  
Have fun :)

I thought that ENVY was a COMPLETE driver installation process unto itself.  In any case, I had already tried using ENVY and when I did I got the exact same results that I did when I initially tried enabling restricted drivers from Gutsy admin. menu, which I assume downloads and installs some type of driver directly from some Ubuntu source.  The result was again, that the maximum resolution I had available to me was 800 x 600, whereas before I started all of this I had 1280 x 1024.  That seems sort of like going backwards to me.

Thanks.

---

### Post by opscure on 2008-04-01
Fix Resolution How To 
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

