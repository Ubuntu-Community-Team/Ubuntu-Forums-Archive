---
title: "Trouble connecting to ONE WiFi network!"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by AndrewZorn on 2008-01-14
Long story short: I installed Ubuntu on my new cheapo laptop and am very happy with it.  I got the wireless working.

I cannot connect to my school's wireless internet.  They say you need to register your MAC address with them.  I did (eth1, the wireless), and it matches what they have now.

It doesn't work!  It doesn't even see it.  A couple of times with playing around and "Connect to other wireless network" (which, I swear, simply makes the icon disappear sometimes, forcing me to restart) I can connect to it but it instantly disconnects.

I've not had trouble with any other wireless network... which isn't many, but still, I've tried unsecured, secured, even right right now I'm connected to the wifi hotspot created by my PHONE!

What could this possibly be?  Why my college network?

---

### Post by coggins on 2008-01-14
Is your school using WPA encryption?  This can be problematic in some cases if you are using the standard network manager applet that comes with ubuntu.  Try "wicd" [http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/") and see if that helps.  If not, post back with some more specific info about your hardware, software versions and as much as you can find out about the school network.  
Someone who knows way more about this stuff than me will be able to help you.

---

### Post by self-defence on 2008-01-14
Ok, do they use any kind of other security measure besides mac address restriction? Is your network card set to a specific IP address manually? Have you tried #ifconfig eth1 up/down ? 

Hope you get it sorted out.

Bye

---

### Post by ugm6hr on 2008-01-14
If you can't "see" the wifi network - it is probably because the don't broadcast the SSID.  If so - Network Manager won't cope well.

Other things that can be difficult: passphrase (ASCII) vs passcode (HEX).

Maybe let us know what security this network has, and we might be able to help with ideas.

---

