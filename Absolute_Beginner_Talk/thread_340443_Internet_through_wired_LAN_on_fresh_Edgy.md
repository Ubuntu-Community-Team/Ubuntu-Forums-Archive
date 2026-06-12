---
title: "Internet through wired LAN on fresh Edgy"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by boywander on 2007-01-17
Hi, people. :)

Yeah, first Linux, a fairly hazy grasp of networking (technically anyway), and dual-booting with XP on ethernet LAN (through a firewalled Linksys router and Binatone ADSL modem/router, which have been all sorts of fun to set up for XP before now).

I don't know whether I need to install any networking drivers for my board (DFI LP UT SLI-DR), or mess with the windows network yet (dual-booting with pre-existing install). Hopefully not. Only the Ubuntu installation is concerned though.

Just want to get online and find a package manager to make things easier. Appreciate any help - couldn't find anything, guides etc, that quite fitted.

---

### Post by doerum on 2007-01-17
hi. 

Have you tried to enable the wired ethernet in System -> (don't remember) -> Network? 
I'm not using ubuntu right now, while at work. But enabling it did get my lan up and running.

Hope this helps

---

### Post by boywander on 2007-01-17
Just tried assigning a free IP from the range available for the router, setting DNS addresses (think I got them right, but have to check), etc. Prefer static address for filesharing and a couple other reasons.

 Really just need to work out the other settings, or whether I need to install + configure any drivers or packages before proceeding. If there's a nuts-and-bolts guide somewhere I'll have a look.

---

### Post by deadgobby on 2007-01-17
I wonder if you are using Point-to-Point Protocol over Ethernet or PPPoE with your ADSL. 
If so you may want to check
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by boywander on 2007-01-17
Apparently 'could not find Access Concentrator' for either device (believe that was the message? two ethernet controllers on this board, which Ubuntu found from the beginning). The connection type given in the modem/router settings, in it's UI, is PPPoA VC-Mux if it helps.

edit - saw photocatcher's thread on the same problem and router (this one is model WRT54G), I assume those packages are on the CD?
 [http://www.ubuntuforums.org/showthread.php?t=340200](http://www.ubuntuforums.org/showthread.php?t=340200)

---

