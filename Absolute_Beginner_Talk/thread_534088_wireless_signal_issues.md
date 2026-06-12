---
title: "wireless signal issues"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by dsbw on 2007-08-24
I'm having a trouble I see reported elsewhere on this forum without any solutions applicable to my situation.

Using Ubuntu 7.04, I'm trying to connect (using a card with an Atheros chip) to a Belkin N1 router. The signal is fine according to a Windows laptop positioned in the exact same location. (Card and router both purchased as a result of trying to get wireless going on Ubuntu.)

I got everything working last week, with a reported signal between 20-30%. The connection would drop from time to time, but it would pick up again pretty quickly in most cases. Yesterday it stopped working. 

Now, if I hover over the bars, I'll get a reading that says "Wireless connection to "mynet" x%" but I'm getting no DHCP address (I usually need 20%+ to get DHCP). I've tried turning off roaming but then I can only put in a WEP key (I'm using WPA2 and picked this card for its support, and don't really want to mess with wpa_supplicant).

I don't know why it's so variable (as high as 35% and as low as 7%) and I don't have any great ideas how to fix it except maybe trying to move the router into a different room (which, when reading that others are getting weak signals right on top of the router, doesn't fill me with optimism).

Now what?

---

### Post by deep-z on 2007-08-25
Check if you have correct driver for that card and maybe (if it's supported by a router itself) turn on maximal signal strenght on a router.

---

