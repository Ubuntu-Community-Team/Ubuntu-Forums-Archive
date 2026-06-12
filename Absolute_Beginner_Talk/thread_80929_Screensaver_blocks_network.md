---
title: "Screensaver blocks network?"
date: 2005-10-23
forum: Absolute Beginner Talk
---

### Post by MasterPatricko on 2005-10-23
I installed Ubuntu Hoary on my computer (which was previously SuSE) and got it working fine. Ethernet card detected and internet perfect. I installed Firestarter and it seems to be working fine. I set up Samba and got it to be the WINS server (Yes, I know what I'm doing) for my three other computers and that worked fine, and I made sure Firestarter had rules to allow the traffic. Everything was absolutely fine. 

However, when the Ubuntu computer went into screensaver or standby mode, the other computers started complaining that the server was unavailable. I came to the conclusion that the screensaver blocks all network traffic - is this correct? Is there some way to make it allow network traffic during screensaver? Right now I have turned off the screensaver and I physically turn off the monitor when I leave the computer - not what I want to do.

---

### Post by queenorych on 2005-10-24
that's crazy talk.  The only thing I can think of is you have some fancy 3d screensaver on an old 486 server.

---

### Post by patrick295767 on 2005-10-25
[QUOTE=queenorych]that's crazy talk.  The only thing I can think of is you have some fancy 3d screensaver on an old 486 server.[/QUOTE]
 
Interesting to have a look, on our linux box tooo ... 
  
Investigation Investigation ...

---

### Post by MasterPatricko on 2005-10-25
Could it be something to do with the Firestarter firewall blocking traffic in screensaver mode?

---

### Post by clearnitesky on 2005-10-25
Actually I've got the same problem. Well, that is my network kept going down for no reason at all when I left my computer for a while (which causes the screensaver to kick in). I'm not using Firestarter or anything like that, it's just a simple ethernet connection to my ADSL modem...

---

