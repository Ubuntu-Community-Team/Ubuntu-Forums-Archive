---
title: "[SOLVED] Yep... One more about wireless problems..."
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by PatsyPoo on 2008-04-12
I have looked EVERYWHERE to try and work this out and I just can't find an answer... I'm working with a Dell Inspiron 6400 and it's got the blasted BCM4311 wireless card. Which seems to be on and recognised by ubuntu. However as soon as I tick **ENABLE WIRELESS** through the network connections icon (top right) so I can try to find my wireless router, the light goes off - which means the card's been turned off as well... I installed ubuntu today so I'm very new at this and have no idea what I'm doing. But I'm not a quitter! I've been trying to fix it since about 5pm and it's now 12:22am. I have finally given up and am going to bed.
Please can someone take pity on me and help me before I have to go back to Vista?! :(
Thanks!

---

### Post by twist2b on 2008-04-12
I'm happy your trying. You can try using nautilus method.

did you goto restriced driver manager though right?

sudo apt-get update
sudo apt-get install ndiswrapper

then use this guide:
[http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)

ignore the part about installing nautilus since you have it already.

---

### Post by Tom--d on 2008-04-12
Install ndisgtk as well with ndiswrapper 

Its the GUI of ndiswrapper. 

[http://packages.ubuntu.com/gutsy/net/ndisgtk]("http://packages.ubuntu.com/gutsy/net/ndisgtk")

---

### Post by PatsyPoo on 2008-04-13
Thanks guys! But I've tried all those that you suggested... Still nothing... Still turns itself off as soon as I Enable Wireless...
Have I no hope?!:confused:

---

### Post by Tom--d on 2008-04-13
Is there a switch on the laptop? Is it on or off?

---

### Post by PatsyPoo on 2008-04-13
When I first booted up on Vista after all the messing about, the light was still off. I hit the Fn button + F2 and it turned itself on. Thinking my brain was no longer working because of the amount of time I'd spent trying to sort it out, I booted Ubuntu up again but it doesn't work...
Thanks again anyway!

---

### Post by Michael.Godawski on 2008-04-13
This may hurt:

I had also a bcm 4311 wlan card in my Dell laptop. I tried every possible guide, ndiswrapper, restricted drivers, and what not. Nothing had worked although there are users who report success stories with the ndiswrapper method. The drivers for the broadcom devices are closed so there must be reverse engineered and the compatibility is not optimal yet. 

So it may work, but it has not to.

My only solution which worked was to open my lapptop, remove the broadcom card and plug in a usb wlan dongle. Now my wlan works perfectly without a hitch. 

I have spent 2 months fighting with the broadcom device before removing it physically.
You have to decide for yourself which way you go.

---

### Post by PatsyPoo on 2008-04-13
That's what I feared!
Thanks for the reply Michael! It was exactly what I feared but hey... C'est la vie, eh?
Maybe next time!
Thanks anyway!

---

### Post by PatsyPoo on 2008-04-19
The one thing I hadn't tried was this [HowTo]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"). Now that I've tried it, the card is enabled and working perfectly. I'm still having trouble connecting with my modem but I know there's nothing up with the card because it detects several wireless networks around here...

---

