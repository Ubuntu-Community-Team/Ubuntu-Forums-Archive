---
title: "i need wifi help"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-08-18
this isn't a matter of "it doesn't work", it's a matter of "i don't get it". yesterday, i too my laptop to work. i opened up wifi-radar and found a few access points (is that what they're called?). i tried to connect to them, but would get couldn't find ip address. i tried the same thing with kwifimanager and gnome's network-manager. i have no problem connecting at home, but i can't seem to figure out what info i'm missing for these other connections. when i use network-manager, all i know to do is set it at dhcp (vs. static ip) and hexidecimal (vs. plain something with a bunch of letters) and the network name. shouldn't this be enough for some other network? 

ps. i'm hoping for a solution that sounds like "first you go like this, then you go like that, hit 'ok' and your done".

---

### Post by Metacarpal on 2006-08-18
It's pretty likely that the wireless access points you're detecting at work are set up with WEP or WPA protection to prevent unauthorized access to the network.

If it's your workplace's wireless, you can likely get the encryption key from your IT dept.  Then you can enter it in either WifiRadar or network-manager.

It's also possible that, rather than assigning you an IP address through DHCP, the networks you're detecting use set IP addresses.  In that case, you'll need to get an IP address and subnet mask from the IT guys, then enter them in WifiRadar or network-manager.

---

### Post by fuscia on 2006-08-19
IT dept.? lol! i work at a music school where no one has the faintest idea how to work a computer. i contacted system76 about this and i'm guessing i'm just being a r*t*rd about it all.

---

### Post by NewDisciple on 2006-08-20
It's still most likely a secure net.  I have three near me which are all encrypted thus I am unable to connect with them.

---

