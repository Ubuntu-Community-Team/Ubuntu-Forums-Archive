---
title: "Headless Wireless Server Help"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by obermeister on 2007-08-24
Ok, my objective is to turn this old dell box into a wireless, headless, server that I can log into remotely from my main PC on my home network.  

I've got it set up with Feisty Fawn 7.04 and running NXServer.  I've put NXClient on my PC and I can login remotely.

The only catch is that I seem to need to log in and connect to my wireless network before I can connect via NXClient.  Since I want to have this box sitting headless in another room, this is not optimal.

I've tried installing Wicd 1.3.1 in place of network manager.  Wicd claims to start up as a daemon, but I think it might be having some trouble.  When I log into the machine, I see the Wicd tray icon, but it shows that it doesn't see any wireless networks.  When I open Wicd itself, it shows "no networks detected", but once I hit the "refresh" button, my network pops up right away (even with the WEP key filled in and the "Automatically log into this network" box checked, ironically).  I can then press the "Connect" link and I'm online.

Obviously, until I get this little wrinkle worked out, my dreams of headless, wireless server will go unfulfilled.  Don't know if there are any WIcd experts out there who could give me a hand.

---

