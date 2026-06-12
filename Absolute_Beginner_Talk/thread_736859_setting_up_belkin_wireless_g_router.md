---
title: "setting up belkin wireless g router"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by colinuta06 on 2008-03-27
my belkin worked fine when i was using windows, but now that i've installed ubuntu, i can only connect to other people's wireless networks that are in my apartment complex... ubuntu is not even detecting my belkin.  how do i go about fixing this so i'm no longer 'stealing' people's internet who don't have passwords?

---

### Post by iSplicer on 2008-03-27
Hmm... What encryption method are you using? Ubuntu should actually pick it up fine

---

### Post by colinuta06 on 2008-03-27
I honestly don't remember, I set up the belkin so long ago.  I was going to plug in directly to the belkin with my network cable but I don't remember the IP to access it to change it's settings.

---

### Post by niteshifter on 2008-03-27
Hi,

Time to reset the router to factory defaults. Google is your friend on this :) as how - exactly - to do this varies. In general: Look for a hole that's is not a air vent hole, which should have a switch behind it. You need to:

Disconnect all wired devices first.

A) With the router powered, press and hold the switch for 30 seconds (some "take" the reset quicker than others, some do take that long).

B) Press and hold the switch, then power up the router. Also hold the switch for 30 seconds or so.

A or B usually works - but no guarantees. "Unresettable" Belkin routers+Wireless Access are not unheard of.

As to Ubuntu not seeing the wireless access point, that's frequently because the broadcast SSID feature has been turned off. Turning this broadcast off is commonly recommended as enhancing one's wireless security. It doesn't enhance security, it does provide some privacy if turned off. SSID = "human name for this access point". Turning it off just means *people* can't' see it. The BSSID is always broadcast (the binary "name" of the access point).

---

### Post by Austin_KW on 2008-03-27
> **colinuta06 said:**
> I honestly don't remember, I set up the belkin so long ago.  I was going to plug in directly to the belkin with my network cable but I don't remember the IP to access it to change it's settings.

Default belkin address is [http://192.168.2.1](http://192.168.2.1)
default password is blank
You should be able to go to the wireless page and see the configuration, make sure that you are not hiding the SSID

---

### Post by ghost_ryder35 on 2008-03-27
plug an ethernet cable in the back of the wireless router
log on to it
and do what ausin said make sure you are broadcasting

-or-

if you know the SSID click on your wireless icon and then say "Connect to Other Wireless Network"
Fill in all of the information requested and your good to go.

---

