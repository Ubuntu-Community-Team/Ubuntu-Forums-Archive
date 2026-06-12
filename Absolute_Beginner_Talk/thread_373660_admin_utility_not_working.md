---
title: "admin utility not working"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by Djembe on 2007-03-01
I'm running Dapper and somehow screwed up the admin utility.  here's the story:

everything was working fine **until** (big dramatic pause) I changed the config for my wireless adapter. I only noticed later that I could make different configuration settings to connect to different networks, so I changed the default config settings from my home router to a different one.  The other network was giving me a somewhat patchy signal, so I disabled the wireless card (eth1).  When I got back home, I tried to reconfigure the wireless card to my home network, but Ubuntu saw it as an ethernet port and wouldn't let me put in information for signal name & encryption.  I looked around and saw that there were settings left over from the previous connection (with the patchy signal), so I deleted all the settings on eth1 from inside the networking panel (I did not touch anything in hardware control).  From then on, not only can I not get into the networking controls, but I also can't get into anything else that requires the administrator popup and password insertion (synaptic, software manager, hardware control, etc.)  When I select something from the "admin" list, the bottom taskbar will indicate that the admin utility is starting as well as my selection, but no windows pop up, and both notifications go away.  When started through Terminal, the programs are blank and unresponsive.  I looked through aptitude, but I couldn't figure out which package contained the admin utility, and I can't set up networking or any other program that requires admin rights without it.  Suggestions?

---

