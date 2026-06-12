---
title: "SBC DSL and Ubuntu"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by Kulluminatii on 2006-10-26
By tomorrow I will have finally upgraded from dial-up to DSL (At&t/SBC to be specific) and was wondering if it was possible to set it up on an Ubuntu machine and will it be fairly easy?(then again, i dont think it will be):p

---

### Post by blendmaster on 2006-10-26
Mine was detected automatically, but it really depends on your ethernet card.

Most are auto-detected by Ubuntu, so you shouldn't have to worry.

It's dial-up that causes problems! ;)

---

### Post by yabbadabbadont on 2006-10-26
The only problem you might have is that, by default, the DSL modem handles the PPPoE login itself and they supply a windows utility to set the username and password in the modem's firmware.  Then the modem acts as a DHCP server for your NIC.  Just make sure you get a modem that supports an ethernet connection instead of USB.  You can set the username and password from linux by pointing your browser to the IP address printed on the bottom of the modem.  You can then change the username and password used to login to your SBC account.  The modem will ask you for the security password that is also listed on the bottom of the modem before it will let you change them.

---

### Post by Kulluminatii on 2006-10-26
Well I purchased a router to use DSL both on my main Windows XP system and on my Ubuntu machine, all I need to do is buy an antenna that will receive the DSL from the router and I will be able to use DSL on both computers. Does anyone have anything similiar to this set up? Did you have any problems?

---

### Post by Kulluminatii on 2006-10-27
Anyone?

---

### Post by blendmaster on 2006-10-27
I doubt that connection will make any difference, as it's still through your ethernet card.

I don't think you have anything to worry about.

---

### Post by rfruth on 2006-10-27
My Ubuntu box and G3 iMac share my wired Linksys router (ATT DSL) no problem

---

### Post by Kulluminatii on 2006-10-27
Cool, I have a Linksys router as well, I feel positive it will work now. Thanks for all the help guys.

---

