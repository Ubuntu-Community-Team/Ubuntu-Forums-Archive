---
title: "Ubuntu strangely slow, wow hangs, and I haven't a clue"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Kenjitamura on 2007-08-24
So ubuntu used to be a dream for me, way faster than windows and did everything I wanted.  Now it has slowed down to the same speed as my windows was.  I honestly haven't a clue as to what happened as it just started a couple days ago for no apparent reason.  Just yesterday I installed another gig of ram into my laptop to see if that'd help and it almost seems as if it worsened the problem.  I ran the top command and the only application that seems to be using any cpu power is Xorg at around 5%.  Firefox even now takes up to 6 seconds to appear.  World of Warcraft use to be a cinch but now when i try to run it there is only a box screen with no response even after a couple of minutes with the error that it's not replying.  I use my system to download up to 300 mb of videos at a time through torrent, use wine for mp3 search and WoW, and disable my firewall every so often when I think the internet may be slowing down.  The only hints I have are that WOrld of Warcraft seemed to be the first to suffer with the occasional internet drop, I installed another gig of ram (after the fact), and I use wine quite a bit as well as torrents.  I used the /etc/hosts tweak and helped a TINY bit.

Please help a noob, I'm willing to run terminal diagnostics etc. and would be very grateful for information on any files that may be the culprit.

System Specs:
1.4 Ghz Pentium M
40 GB HDD
1.5 GB Ram
Nvidia Graphics card with dedicated memory
(Use a laptop cooling pad)

---

### Post by Kenjitamura on 2007-08-24
Sorry to double post but here is an update.  My system is running faster now on its own (go figure) and I may have found the solution to WoW.  Apparently Blizzard is running a survey today and it is blocking ALL wine using WoW players from getting past the login screen (yes I can also reach the login screen now).  So If i configure the wtf/Config.wtf file to exclude the line SET gxApi "opengl" and run WoW the survey will let me through in Direct 3d mode then if i logout right away and re add the line the problem will be fixed.  I'm going to try now.

---

