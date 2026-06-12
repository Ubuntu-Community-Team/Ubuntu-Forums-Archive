---
title: "Ubuntu as a Wireless AP with WPA"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by SlowRedFox on 2007-08-24
After recently buying a new computer, I decided to turn the old outdated one into an all-terrain router and server running Ubuntu. 
So far, I have have had great success, with the wired routing working (nearly) perfectly, but now I have come to a full stop in front of the wireless networking minefield. I want this router/server to act as an access point as well, and there are several good tutorials around the place for this - however, they all use WEP, which is not a hole I am willing to step into. How would I go about creating an access point with WPA rather than WEP? 
 
The computer has 2 wired network cards, one of which connects to a modem in bridge mode, the other being the ethernet connection. The wireless card is a Dlink DWL-G520, based on an Atheros chipset, which I have succeeded in getting into master mode without having to destroy and recreate the interface. However, the rest of the configuration seems less simple. 
I have found hostapd, which looks like it could be a solution, however, the configuration is currently beyond me. 
 
I should also note that I'm currently running the server in command line mode, with no x-server or window manager installed. I would prefer to keep it that way, if at all possible, as it has taught me a lot about Linux and Ubuntu!

---

### Post by Vadi on 2007-08-24
I'd recommend that you move this thread to here : [http://ubuntuforums.org/forumdisplay.php?f=136](http://ubuntuforums.org/forumdisplay.php?f=136), you'll get more help there :)

---

### Post by milosz.galazka on 2007-08-24
In the mean time look [here]("http://linux.sys-con.com/read/46902.htm")

---

### Post by SlowRedFox on 2007-08-25
Thanks, a combination of that last site and a few others did the trick.

---

