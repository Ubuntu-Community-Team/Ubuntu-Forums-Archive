---
title: "Linux n00b needs to get wireless card working!"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by mwneal on 2006-04-24
Hi all, as the title denotes, I am completely new to Linux and know next to nothing about it. I had installed it on my laptop a little while back (as a dual-boot with Windows), and it looked great! There was one thing I couldn't get working, however, and that was my wireless capabilities. That is the reason (the only reason) I'm using Windows right now.

I'm determined to switch back to Ubuntu, but only if I know I can get this working. I'm looking to install Ubuntu on a Dell Inspiron 2200 laptop with an Intel Internal Wireless 1370 WLAN Mini-PCI Card. Everything else works well for me (audio, video, Ethernet connection, etc.), I just need to get wireless working.

Any help I could get on this would be greatly appreciated. :)

---

### Post by nalmeth on 2006-04-25
No one has replied after 2 hours? Weird..
Don't know first hand enough to walk you through this, but this link should help you out, if you don't mind a little reading:
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide]("https://wiki.ubuntu.com/WirelessTroubleshootingGuide")

Try going into SYSTEM - ADMINISTRATION - NETWORKING
see if wlan0 or something similar is there, and try to activate it.
There is an app called ndiswrapper which can use windows wireless drivers and make them work, if the device is supported.
ndiskgtk is the graphical interface for it.
Can you plug the machine into ethernet for any time frame?

---

### Post by Jagot on 2006-04-25
Heya, you're going to need ndiswrapper and the Windows drivers for the card.  I have a Dell Inspiron 1300 with the 1370 wireless card, but for some reason the Windows drivers that came with my system didn't work with Linux so I had to download the drivers for the card from Acer.  I got the card working as is described in this post:

[http://ubuntuforums.org/showthread.php?t=120383](http://ubuntuforums.org/showthread.php?t=120383)

---

### Post by TrojanSkin on 2006-04-25
[http://www.ubuntuforums.org/showthread.php?t=162587]("http://www.ubuntuforums.org/showthread.php?t=162587")
Should help you. Good luck. By the way, if you're using Kubuntu, God help you!

---

