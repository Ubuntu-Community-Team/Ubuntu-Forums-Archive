---
title: "X Crashing and restarting over and over"
date: 2015-12-15
forum: Apple Hardware Users
---

### Post by rough68fish on 2015-12-15
I already figured this out but wanted to post to save the next guy some time and effort. I got two (free) G4 iMacs for my daughters (6-7) for Christmas and want them to run Ubuntu. My son (8) is on and old PC running 14.04 and loving it he makes his own Minecraft cartoons in Scratch.

I installed 14.04 LTS (Trusty Tahr) using the Alternate Install ISO on a 20" G4 iMac. After it would boot it would go blank (as X was trying to start) and then flash back to the text console showing an error from the nouveau video driver (I will add the exact text). I thought this meant I had a problem with the driver setup and went down the path of messing with yaboot parameters and creating a very specific xorg.conf file.

Not entirely worthless since I understand a lot more about this now, but that wasn't the problem. I eventually decided that the driver was ok because booting single or doing ctrl-alt-F1 gave me a perfectly workable console. Then I started messing just with X and I wanted to get the machine to boot into a multi-user text mode so I was trying to turn off gdm (which I could see was starting X). 

I tried removing the links from the init.d directories but X would still try to start on boot. 

Out of frustration :( I decided to remove gdm (apt-get remove gdm) from the system and low and behold on reboot it started with lightdm and the GUI login prompt appears. 

My guess is that I got both installed during the Alternate Install process (probably the last screen) and they can't be installed together. 

Any further insight would be appreciated. Now to get the sound working.

--Sean

---

