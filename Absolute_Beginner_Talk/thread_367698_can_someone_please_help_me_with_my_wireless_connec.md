---
title: "can someone please help me with my wireless connection?"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by leao on 2007-02-22
I new to Linux and not especially good at computers. I've installed ubuntu successfully but can get wireless internet.
I have tried the ping test in network tools and that seems to be ok. If i not mistaken, that means that the connection between the computer and the router is alright. 
So i tried the DHCP configuration in the ubuntuguide wiki but it comes up with an error saying

(gedit:18597): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
 
My wireless card is a PRISM 802.11g Wireless Adapter

I would be very grateful for any help.

---

### Post by nickoli_02 on 2007-02-22
Make sure you're using WEP encryption on your router and not WPA. In order to get WPA working you'll need to go through some additional configuration with wpa-supplicant.

---

