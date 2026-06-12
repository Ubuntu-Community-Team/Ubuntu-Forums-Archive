---
title: "Internet connection probs in Kabuntu"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by dreager on 2007-03-06
Hi,

Total Linux Noob here. Finally got partitioned, (dual-boot with XP) and love the whole set up using the Kabuntu DVD 6.10.

I dutifully followed previous archived posts by typing sudo pppoeconf in terminal and all went went well 'till I tried using kabuntu browser and the old error destination not reached for [Http://www.yahoo.com](Http://www.yahoo.com). I typed in "Plog" and it says padd,intitialized server rejected login. Not exact wording, but basically saying it's not connected. (should have written down but...)

Mine is a basic system , Alcatel speed stream dsl modem connected to one computer via ethernet cable on a Intel P4/500 ram/SMC ethernet card. I use a login name and password. Prior to all of this I tried using "network" from system and installed dns numbers etc. which I thought may have caused this. I went back in and reset what I could to defaults, which shows 10.0.0.138 now. I deleted any server info I had put in too. I rebooted when I first got "Not connected" error, but that didn't fix it.

No problem connecting in XP.

---

### Post by marko_4454 on 2007-03-06
You need to add these DNS servers. It should work...

208.67.222.222
208.67.220.220

System >>Administration>>Networking>>DNS
and add those servers.
These servers are for "Opendns" more info go to...
[www.opendns.com](www.opendns.com)

---

