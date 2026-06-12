---
title: "[SOLVED] Solved: Kubuntu 7.10 openoffice and firefox"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by kle on 2007-12-07
Using Kubuntu Gutsy (7.10) dual boot on laptop HP Pavilion 6000

I would just like to conclude that the freezes I had on Firefox (cold) and Openoffice (which would not open but which could be killed kindly) are no longer a problem. What I did: 

1) reinstalled Kubuntu Gutsy adding "noapic irqpoll" in grub menu
2) disabled CD from sources list
3) ran sudo dpkg --configure -a 
(to clean up repositories)
4) updated all Gutsy's proposed updates except OpenOffice and Restricted drivers

Openoffice ran ok, but refused to allow me to install my language dictionaries
Firefox ran ok for an hour without freezes, and is still running.

I then 
1) added my own languages in system
but openOffice still did not find the spell check of my language.

So
I finally allowed update of Openoffice in Adept Manager
and also installed (without enabling) the restricted drivers. 

Open Office has now allowed me to get the dictionaries and is working fine. 
Firefox seems to be working just fine, but I shall be wait a while before installing add-ons. 

So now everything seems fine. I am still "isolating" restricted drivers for a while. 
Thanks for invaluable help from Herman on [http://www.users.bigpond.net.au/hermanzone/](http://www.users.bigpond.net.au/hermanzone/)
and support here on the forums.

---

