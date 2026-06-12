---
title: "Newbie to Linux having no luck with DWL120 usb adapter wifi! Help!"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by jin8k on 2007-11-27
Hello All!

Need absolute help before I go back to windows xp for the next 6-12 months waiting for my exhausted guts to refill to attempt another migration to LINUX!!!

I downloaded ubuntu 7.10 and installed on a partition.
Now I have problem with wifi, my usb adapter is D-Link DWL120 and got 2 routers, one airport express, and the other is USR9110.

Airport is set to wpa and usr9110 is set to wep hex 10 digits.

I can see at the beginning the two routers along with other signals from the neighbors, but when I provide the wpa or wep, none of the signals are picked... if some weirdly the signal is picked, IP is set to 0.0.0.0.

I am a complete newbie to LINUX, but help me with my wifi plz!!!

---

### Post by jin8k on 2007-11-27
Solved...

Nevermind... by using some bunch of codings in terminal, sudo sudo sudo sudo sudo:)

Link to solution, in Italian: [http://forum.ubuntu-it.org/index.php/topic,47690.0.html](http://forum.ubuntu-it.org/index.php/topic,47690.0.html)

---

### Post by V3M4 on 2007-11-27
I'm a total noob too. But what better way to learn than to try and help others, so here goes.

I had the same problem, although I was using an internal wireless card. At first I thought the card drivers were incorrect, but the fact that it was able to see other wireless networks keyed me in to the fact that it was working and I wasn't getting a valid ip address.

Unfortunately I had changed a bunch of settings on my wireless router and threw too many variables into the problem. The problem ended up being the dhcp settings on the router, I opened up the tables to allow enough addresses for my 2 machines at home but it was seeing the new OS and new wireless card as a seperate connection.

I solved my problem by reviewing my settings on the router, setting everything back to a known good state, verifying the connection through my other boxes, and then rebooting my Ubuntu box. When I connected to my network I used my passphrase instead of the actual key and everything connected just fine. I checked the router status and could see my machine in the dhcp tables.

Hopefully this will help you move in some direction.

---

