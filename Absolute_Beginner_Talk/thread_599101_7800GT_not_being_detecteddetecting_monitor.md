---
title: "7800GT not being detected/detecting monitor"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-11-01
I recently put my 7800GT that I had lying around into my ubuntu system and now I can't get the drivers to work properly.  When I start up it says that it cannot detect the card/monitor so it will switch to low graphics mode.  Can anyone help?
P.S. I am also using a DVI-VGA adapter.

---

### Post by overdrank on 2007-11-01
> **Dapman01 said:**
> I recently put my 7800GT that I had lying around into my ubuntu system and now I can't get the drivers to work properly.  When I start up it says that it cannot detect the card/monitor so it will switch to low graphics mode.  Can anyone help?
P.S. I am also using a DVI-VGA adapter.

Hi and do you have onboard graphics also and have you tried t reconfigure your xorg?
And have you tried Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Dapman01 on 2007-11-01
I will try that, but I think the reason why was because I didn't have a six-pin pci express pin plugged in.  Do you think that that is the problem

---

### Post by DezSP on 2007-11-01
It's most likely because Ubuntu's Xorg config is too new and too glitchy. It claimed my monitor (on a 7900 GS) ran at 74 Hz instead of the actual 60. :/

I'd recommend the old fashioned way:

```
sudo dpkg-reconfigure xorg
sudo gedit /etc/X11/xorg.conf
```

There are plenty of old howto's on setting up X.org, so just search around for one of those, but it's pretty straightforward.

---

### Post by overdrank on 2007-11-01
> **Dapman01 said:**
> I will try that, but I think the reason why was because I didn't have a six-pin pci express pin plugged in.  Do you think that that is the problem

And yes that would cause some issues with the power. Good luck!

---

