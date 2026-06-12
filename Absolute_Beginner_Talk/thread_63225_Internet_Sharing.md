---
title: "Internet Sharing"
date: 2005-09-07
forum: Absolute Beginner Talk
---

### Post by Stadic on 2005-09-07
Hi,

I've got a PC running Ubuntu that's *not* connected to the internet and a PC running XP Home that *is*, via a cable modem. I have an ethernet cable and each PC has a functioning network card.

I want to use the Windows PC to share its internet connection with the Linux PC. I hooked the two up last night and ran the XP network wizard but it couldn't seem to see the other computer, and vice versa.

Is what I'm trying to do possible and if so how the hell do I get it to work?

---

### Post by KingBahamut on 2005-09-07
Use your Ubuntu PC as your primary machine. 
Making sure you have the repos from ubuntuguide.org 

apt-get install firestarter 

Run it , configure it, and enable connection sharing on it.

You can enable connection sharing on XP, but, This isnt supported in this forum, and most certainly not by me, but you can ask.

---

### Post by UbuWu on 2005-09-07
While it should be perfectly possible to do this with windows, routers are not expensive anymore these days and could be a better idea (easy to set up, no need to keep the windows pc on for internet on the linux pc).

---

### Post by Stadic on 2005-09-07
It worked! Thanks alot.  :)

---

