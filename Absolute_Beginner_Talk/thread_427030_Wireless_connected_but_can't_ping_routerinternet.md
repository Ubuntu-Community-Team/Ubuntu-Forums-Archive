---
title: "Wireless connected but can't ping router/internet"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Game_boy on 2007-04-29
I have a WEP secured network which I the Network Manager found, asked me for a hexadecimal password and then connected to at 95%. iwconfig confirms the connection's on wlan0.

However, I can't ping my router or any internet site! My router is fully operational with any other computer, though. 

Any ideas?

---

### Post by Game_boy on 2007-04-29
It also can't ping 127.0.0.1

---

### Post by riminicat on 2007-04-29
what version of ubuntu are you using?

---

### Post by Game_boy on 2007-04-29
Feisty.

---

### Post by octoberdan on 2007-04-29
What's the result of iwconfig?

---

### Post by riminicat on 2007-04-29
unfortunatly feisty is having wireless issues right now, it only works on and off.

---

### Post by riminicat on 2007-04-29
octoberdan can help you, he knows more then me

---

### Post by Game_boy on 2007-04-29
iwconfig shows normal connection on wlan0

---

### Post by octoberdan on 2007-04-29
> **riminicat said:**
> octoberdan can help you, he knows more then me

Hehe, I'll do what I can while I can (it's 4am here and I haven't slept)

Would you mind also providing the exact result of ```
ping 127.0.0.1
```. Unsure of what you mean by "fails". Also, what wireless card are you using?

---

### Post by octoberdan on 2007-04-29
> **Game_boy said:**
> iwconfig shows normal connection on wlan0

Could you please copy and paste? If you have a floppy disk or something you can use that to transport the info.

---

### Post by Game_boy on 2007-04-29
Well it would take me 10 mins. to reboot to ubuntu & back to tell you the ping result, but firefox just said it can't establish a connection which I assume means no response.

Er.. I'm using a USB adapter? The router's called a Belkin F5D7632.

---

### Post by Game_boy on 2007-04-29
Well... ping 127.0.0.1 does work now for some reason, but ping 192.168.2.1 (my router) has "Destination Host unreachable"

And typing 127.0.0.1 in Firefox returns "can't find the page"

---

### Post by joneil1000 on 2007-04-29
I am having similar issues on my laptop (Belkin card, Ver 7.04).  I use both the Network settings under Sytem-Admin-Network, and i use setting under the program WIFI Radar.

     The issue I get is WIFI Radar shows me connected to my wireless (WEP security), but no IP address.  To get an IP address, I have to go System-Admin-Network, and change my password or security code (whatever you call it) under WEP from ASCII to HEXIDECIMAL.  Then that works for a while.  

   Then next day, or even later that same day - form the exact same location, I have to go in, same route, and change fomr HEXIDECIMAL to ASCII.

    Then to top it all off, in WIFI Radar, I go into 'EDIT", and i ahve to add WEP code to the WPA "Driver" box to connect.

   I can easily detect other networks in my area - in fact, I have way too many networks in my neighbourhood (66 at last count) and some fo them are stronger inside my house than my own network, so I have issues totally unrelated to Ubuntu there.  For example, my other laptop, running XP, has these issues with other networks "crashing" into my house and knocking me off the air.

    But in ver 7.04, the bottom line to me is, especially compared to Ver 6.10, something is wrong in Feisty that it cannot handle WEP and WPA security properly.    I never had this issue in 6.10.

   So to repeat myself - I can connect fine, but I cannot get an IP address under ver 7.04 unless I constantly play with and change the WEP and WPA settings both - even though I am only using WEP at this point.

   My advice is, if you can, install WIFI Radar, and open both it and System-Admin-Network at the same time, play with the settings on both untill you get something to work.  Otherwise I think we have to wait for a patch/repair to fix this issue. 

    Also, if you are like me, and have a machine that cannot connect to the net except for wireless - I have a desktop in that situation - I'm going to re-install Ver 6.10 on that machine because I know it works.

good luck
joe

---

### Post by Austin_KW on 2007-04-29
What type of wireless adapter?

---

### Post by joneil1000 on 2007-04-29
> **Austin_KW said:**
> What type of wireless adapter?

  Belkin PCIMIA wireless notebook card.  I forget the exact model number, but it has the Atheros chipset on it.   I had it working just fine under 6.10 with Ndiswrapper.  Instant connect every time I turned on the laptop.

  I do have a built in wireless card in my laptop, but it never worked correctly from the start, even under XP, but the Belkin card did.  My laptop has a physical slide switch for the wireless card, so I just leave it turned off all the time.  The issue with the non-working wireless card, IMO, had to do with the built in antenna, which would hardly pick up any wireless network, under  XP or Ubuntu, even if you where three feet away from the wireless router.   On the flip side, the Belkin card detects wireless networks a full city block away when I have a clear line of sight.

   Also, everything except seems to work just fine, except for aquiring an IP address.  I can connect to my network instantly, but not get an IP addess - I just get  error messages until I play with the password settings, then i can aquire an IP address.   I can detect other wireless networks in my area.  about the only thing I have not tried is to connect to a unsecured wireless network to see if I can  but that just seems a little wrong somehow.  

   IMO, the entire flaw with Feisty and wireless lies somehow, somewhere in the WEP & WPA connection.    Just wish I knew what it was.

joe

---

### Post by Austin_KW on 2007-04-29
Don't know that card. Mine is the 7010 v3000 but that is the rt2500 chipset.
It has an issue with 7.04 where you have to set the essid when the interface is down but I doubt that it effects the atheros drivers.

I think that I did see issuses where you need to get the atheros driver from the restricted repositories, so searching the forums may help you.

---

