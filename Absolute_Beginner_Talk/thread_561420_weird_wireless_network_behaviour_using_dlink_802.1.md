---
title: "weird wireless network behaviour using dlink 802.11/2.4 Ghz wireless router"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by reyjexter on 2007-09-27
i was able to browse the internet a while ago. i forgot to connect the power chord so i didnt notice that my laptop is already turned off. when i turned it back on i cant seem to browse any webpage but the weird thing is, i'm able to see my wireless network. i rebooted and started my windows xp os (i'm on dual boot) and it did not have problem connecting to my wireless network. 

i tried all the tricks i have read in this forum and i cant seem to get my wireless network working. i'm also not certain if the problem is on my linux os or the router.

pls help

thanks

---

### Post by Mr.Beast on 2007-09-27
> **reyjexter said:**
> i was able to browse the internet a while ago. i forgot to connect the power chord so i didnt notice that my laptop is already turned off. when i turned it back on i cant seem to browse any webpage but the weird thing is, i'm able to see my wireless network. i rebooted and started my windows xp os (i'm on dual boot) and it did not have problem connecting to my wireless network. 

i tried all the tricks i have read in this forum and i cant seem to get my wireless network working. i'm also not certain if the problem is on my linux os or the router.

pls help

thanks

It seems to me that quite a few of these questions that come up are with Dual boot machines, then again, maybe there's nothing in that whatsoever.

On the main Bar along the top (or wherever you have moved it to) you should have a little icon like a set of steps it shows the signal strength of the network you are connected to. 
Now, I have Roaming mode enabled, and this allows me to setup separate profiles. Left click and connect to New wireless network, then enter your SSID, and select the type of encryption you use. it should be job done.

If you can remote onto the router from your windows box, then backup the configuration, then do a hard reset and see if your linux box connects. If it does, then reload the config onto the router and open her up a little.  It could be that the dual boot is hanging on to the ip address and a different workstation name bot the same hardware addresses.  
Try renaming either your windows box to be the same name as your linux box (assuming this is dual boot, right?) or vice versa, whatever you are more comfortable with.

---

