---
title: "Ubuntu 10.10 Trackpad problems on MacBook7,1"
date: 2011-01-20
forum: Apple Hardware Users
---

### Post by katacarbix on 2011-01-20
I tried Ubuntu 10.10 on my MacBook, but I had a few problems. They, surprisingly, were not the problems most people have.
1) The trackpad had the "Tap to Click" setting on, but I couldn't find out how to change it.
2) The clicking was only right click.

I also had a few other problems that I will mention, but you aren't obligated to answer them:
1) I couldn't find my wireless network.
2) BootCamp isn't partitioning, so I can't really install Ubuntu.

---

### Post by theSuperman on 2011-01-20
> **katacarbix said:**
> I tried Ubuntu 10.10 on my MacBook, but I had a few problems. They, surprisingly, were not the problems most people have.
1) The trackpad had the "Tap to Click" setting on, but I couldn't find out how to change it.
2) The clicking was only right click.

I also had a few other problems that I will mention, but you aren't obligated to answer them:
1) I couldn't find my wireless network.
2) BootCamp isn't partitioning, so I can't really install Ubuntu.

I run this command everytime I boot up. It enables clicking and tapping.

```
sudo synclient TapButton1=1 TapButton2=2 TapButton3=3 ClickFinger2=2 ClickFinger3=3
``` (left click is enabled by default so I dont have to manually set it).
You can put it in your /etc/rc.local file (mark it as executable), however my rc.local file doesnt seem to be automatically run on bootup, like it has in every prior version of Ubuntu that I have used (since 6.04).  
Also, did you install the wireless device drivers? Connect your Macbook to your router via ethernet and go to System-> Administration->Additional Drivers.

---

