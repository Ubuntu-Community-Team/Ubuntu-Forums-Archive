---
title: "Finally got WPA working! Got a question though..."
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by Tlingit on 2007-08-23
ok i finally got some where i have the option for WPA!!!! HECK YESS finally. but when i enter my pass key it doesn't work?? any ideas???

---

### Post by Blutack on 2007-08-23
Bit more info and you might get some more answers...
Router?  Wireless card?  Version of Ubuntu?

---

### Post by wormser on 2007-08-23
I just got mine set up today.  My resolution was to reboot a couple of times and try connecting each time.  Every time I made a change to the router my wireless would not update to the changes.  So, I rebooted and then it worked.

---

### Post by Tlingit on 2007-08-23
newest version of Ubuntu (linksys wpc54g ver2.) fallowed the guide to get this particular card to work for the ndiswrapper.
[http://ubuntuforums.org/showthread.php?t=324148](http://ubuntuforums.org/showthread.php?t=324148)

WRT54g ver2 for my router

---

### Post by Tlingit on 2007-08-23
newest version of Ubuntu (linksys wpc54g ver2.) fallowed the guide to get this particular card to work for the ndiswrapper.
[http://ubuntuforums.org/showthread.php?t=324148](http://ubuntuforums.org/showthread.php?t=324148)

WRT54g ver2 for my router

---

### Post by anewguy on 2007-08-24
I have been trying for weeks to get WPA working on my laptop and router.  I couldn't even get WPA working when I had Windows (I'm all Ubuntu now).  I can turn on WPA personal but it doesn't matter what I put in for a pass key (yes - router and PC) it will not work.  It apparently knows about the WPA portion, because if I change the PC to something other that WPA, the wireless light on my router won't light up, but with WPA it lights up and blinks, but always says trying to join the xxxxxxxx network.  I've tried purposely not matching the pass key but it still comes up the same message, which makes me think it just isn't doing anything with the pass key.  

If it helps, I'm running a Gateway laptop and a 2WIRE DSL modem/wireless router.  I tried creating a wpa_supplicant.conf file and still nothing.

If you are having problems with the pass key, perhaps we share a common problem?  I have no idea and gave up and went back to WEP which works fine.

I can't remember if it was Gateway, 2WIRE or my DSL support that said I had to have something called Aegis protocol installed in order to use WPA.  The only things I have found for that cost money, and that kinda defeats the purpose of the principal behind Linux, ya know?

---

### Post by gn2 on 2007-08-24
> **Tlingit said:**
> ok i finally got some where i have the option for WPA!!!! HECK YESS finally. but when i enter my pass key it doesn't work?? any ideas???

Have you tried WICD yet? 

It's the Wireless Utility link in my sig.

It is a replacement for the standard Network Manager.

---

