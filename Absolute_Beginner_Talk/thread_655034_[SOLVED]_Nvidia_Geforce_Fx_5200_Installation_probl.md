---
title: "[SOLVED] Nvidia Geforce Fx 5200 Installation problem."
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by tbobo05 on 2007-12-31
I am having some rather annoying problems while trying to install my Geforce fx 5200 on Gusty Gibbon.  

I just installed the card and everything went great.  Ubuntu booted into a low resolution GUI and asked me to configure my monitor and select my video card, which I did.  I continued into my root account where I installed and ran Envy where everything seemed to go fine.  I also used the Restricted Drivers program and installed and enabled Nvidia's proprietary driver.  

Now here comes my problem.  I rebooted and everything stayed the same as it had been before I installed Envy and the drivers.  It still asks me to configure my card/driver and still runs in a low resolution 800x600 mode.  What am I doing wrong?  I will be happy to supply any further information  you need in order to get this problem solved.  Thanks in advance

---

### Post by alienexplorers on 2007-12-31
Have you tried using the nvidia-settings program.  Run in terminal:
> nvidia-settings
This is used to set your resolution and refresh rate.

---

### Post by overdrank on 2007-12-31
> **tbobo05 said:**
> I am having some rather annoying problems while trying to install my Geforce fx 5200 on Gusty Gibbon.  

I just installed the card and everything went great.  Ubuntu booted into a low resolution GUI and asked me to configure my monitor and select my video card, which I did.  I continued into my root account where I installed and ran Envy where everything seemed to go fine.  I also used the Restricted Drivers program and installed and enabled Nvidia's proprietary driver.  

Now here comes my problem.  I rebooted and everything stayed the same as it had been before I installed Envy and the drivers.  It still asks me to configure my card/driver and still runs in a low resolution 800x600 mode.  What am I doing wrong?  I will be happy to supply any further information  you need in order to get this problem solved.  Thanks in advance

HI and I believe the problem arose when you enabled the restricted drivers after using Envy. You can use one of the installation but not booth ( at least is my understanding and practice) So you may try and use Envy to uninstall the drivers then either try the restricted drivers or Envy but not both. You may also have to reconfigure you xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by tbobo05 on 2007-12-31
Ok, so I uninstalled the Envy Nvidia drivers and went with the Restricted Drivers.  I ran the command to reconfigure my Xorg and I still can not change my desktop from the 800x600 resolution and I still get the same "Ubuntu is running in a low resolution graphic mode" upon startup that asks me to configure my video card / monitor.  

I am now trying to disable the Restricted Driver and I do not see an option; how do I go about that?

---

### Post by tbobo05 on 2007-12-31
Sorry, evidently I had the restricted driver disabled already.  I re-enabled it and everything seems to be working fine now aside from my new super high resolution.  Thanks for the quick reply and help gentlemen (or gentlewomen as the case may be.) :-)

---

### Post by overdrank on 2007-12-31
> **tbobo05 said:**
> Sorry, evidently I had the restricted driver disabled already.  I re-enabled it and everything seems to be working fine now aside from my new super high resolution.  Thanks for the quick reply and help gentlemen (or gentlewomen as the case may be.) :-)

Great, please mark the thread as solved under thread tools and good luck! :KS

---

### Post by Sef on 2007-12-31
> Sorry, evidently I had the restricted driver disabled already. 

I have the drivers fail to load on rare occassion.   I have learned to check the Restricted Driver's Manager first when that happens.

> gentlewomen

This is actually a real word in English though not much used today.  It referred to a woman who was from nobility.

---

