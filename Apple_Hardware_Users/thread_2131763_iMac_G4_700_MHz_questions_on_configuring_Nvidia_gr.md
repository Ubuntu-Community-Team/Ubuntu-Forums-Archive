---
title: "iMac G4 700 MHz questions on configuring Nvidia graphics"
date: 2013-04-02
forum: Apple Hardware Users
---

### Post by Beans445 on 2013-04-02
Hello,

Any help for a Linux noob would be greatly appreciated.

I have installed Lubuntu 12.04 (alternate .iso) on an iMac G4 (aka ilamp, aka snowball) 700Mhz with an Nvidia graphics chip.  Upon boot, I am presented with a blank white screen.  

In Yaboot, I entered the command 'Linux nouveau.modeset=0" based on some information I have googled.  When I do this, I am presented with a low quality image of the desktop with awful colors.  I wish I had the ability to send a screenshot, but I cannot.  

I am trying to follow the Ubuntu tutorial for PowerPC users with Nvidia chips here:  [https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/PPC#fnref-36f402cf367c978c48dae82761e416e72cd464e3](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/PPC#fnref-36f402cf367c978c48dae82761e416e72cd464e3)

However, when I enter the first command on the tutorial "sudo Xorg -configure" I am given an error message because the X server is already active.

Is there a way that anybody knows that I can use to boot directly into CLI and not activate X server so I can make the changes?

Another hiccup is that the link contained in step 6 of the Ubuntu tutorial leads to an inactive link, and the document is not available.

Any help would be greatly appreciated.  I have been tinkering about three days or so, and I am the closest that I have been to getting the computer up and running.

Thanks!

---

### Post by danield on 2013-04-03
You can boot into a command prompt by entering at the second yaboot prompt <tabkey> then "Linux single" without quotes.

See also this: ["iMac G4 700/800 for Dummies"]("http://ubuntuforums.org/showthread.php?t=2131644")

---

### Post by Beans445 on 2013-04-03
Thank you, Daniel!  I was able to log into the CLI and the tips in the post you referenced help me get the video up and running.  :)

Thanks again!

---

