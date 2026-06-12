---
title: "Now my graphics!"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Mazehero55 on 2007-06-19
Wow it seems that just when I fix something, something else goes wrong! 

Well I was doing everyday normal stuff on my computer when suddenly the screen goes black.
(why do I think of the Sopranos?)

Well anyways I was just alittle shocked  for it suddenly going black. I checked the power, I checked to see if the monitor was still plugged into my computer, but everything checked out. So I restarted gnome with ctrl+alt+backspace when it loads back the login screen everything is all screwed up, distorted and black and white.

So I went into command line and put on the xorg.conf.backup then it worked. 

well I figured out it was only when the 3d nvidia driver was on. But it's been working for around 5 months so far without a problem. Why would it now screw up?

I have tried reinstalling the driver and even tried using envy to get it up. 

Does anyone have any ideas?

---

### Post by Mazehero55 on 2007-06-19
anybody anything? Is there any ideas on how to get the 3d driver back up?

---

### Post by shae on 2007-06-19
Set it to use the restricted driver and try booting it.  Once booted, switch to one of the virtual consoles and report the output of
 ```
cat /var/log/Xorg.0.log | grep EE
```
 ```
cat /var/log/Xorg.0.log | grep WW
```

---

### Post by tgalati4 on 2007-06-19
Your monitor may have gone up in smoke.  It happens.

---

