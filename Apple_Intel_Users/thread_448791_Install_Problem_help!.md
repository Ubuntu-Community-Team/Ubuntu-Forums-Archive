---
title: "Install Problem help!"
date: 2007-05-19
forum: Apple Intel Users
---

### Post by dareofficer on 2007-05-19
Hello, I have a intel Mac iMac.  I have OSX 4.9 with all the updates.  I created a 32gb part with boot camp.  I installed Fiesty with no problems.  When I put up with efit, I see a Mac/linux boot.  It boots in to mac just fine, when I try linux, it says no system disc???

What did I do wrong?

---

### Post by ronocdh on 2007-05-20
> **dareofficer said:**
> Hello, I have a intel Mac iMac.  I have OSX 4.9 with all the updates.  I created a 32gb part with boot camp.  I installed Fiesty with no problems.  When I put up with efit, I see a Mac/linux boot.  It boots in to mac just fine, when I try linux, it says no system disc???

What did I do wrong?
Please transcribe the error message completely. Does it appear to be a rEFIt error message or one from Ubuntu, or from GRUB?

---

### Post by dareofficer on 2007-05-20
I got it last night after reading some of your other responses.  I needed to use "Burn" to create the image.  I got it working fine now with one exception.  The video is not at 1680x1050, rather 1400x1050.  How can I change the video?  

All and all it looks and runs GREAT.

Thanks

---

### Post by ronocdh on 2007-05-21
> **dareofficer said:**
> I got it last night after reading some of your other responses.  I needed to use "Burn" to create the image.  I got it working fine now with one exception.  The video is not at 1680x1050, rather 1400x1050.  How can I change the video?  

All and all it looks and runs GREAT.

Thanks
Provided you have the ATI proprietary driver installed and enabled (check in the Restricted Drivers Manager settings panel), use this command in the terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
You'll be able to manually specify the resolutions you want to have listed in your Screen Resolution panel.

---

