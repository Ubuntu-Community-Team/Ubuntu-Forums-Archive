---
title: "nvidia geforce 7300gs issue"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by apureevil1 on 2007-05-24
I recently upgraded to 7.4 and had everything working the way I wanted it (except for my video) So I bought an Nvidia 7300gs PCIe card and installed it, I fought for several hours with it and had no luck so I did what I so often do I DID A COMPLETE rebuild. I decided to try envy and everything is working great except when I reboot, all the settings go away and my resolution is about as big as you can get. I cant post my xorg file now because I am not at my device, I did notice that it is calling my 17" Viewsonic VE175b (LCD) a crt monitor. I have been reading all over the form that I can modify my xorg.conf file, I tried to use the Nvidia tool to do this with no success.I would appreciate any help..Thanks

---

### Post by scrooge_74 on 2007-05-24
what happens when you do

sudo dpkg-reconfigure xserver-xorg

---

### Post by Happy_Man on 2007-05-24
Hmm.... when you get to your comp, could you please post xorg.conf? For problems like this, it's usually the best thing to do. 

Also, did you run 

```
sudo nvidia-settings
```

so that it can save info?

---

### Post by apureevil1 on 2007-05-29
sudo nvidia-settings

seemed to solve the issue, thanks...

---

### Post by theShaggy on 2007-06-08
This continues to be an issue for me, too.

I have tried reconfiguring my xorg manually and also with nvidia-settings, however nothing seems to work.  I installed with Envy and it seemed to install fine.

However, I am having trouble adjusting the resolution above 1024x768 and 50MHz.   I can't seem to configure to read my AOpen LCD monitor as anything but a CRT, and don't know how to go about doing that.

Perhaps I will go in and physically change the xorg config, but I'm scared to screw anything serious up.

Hmm.

---

