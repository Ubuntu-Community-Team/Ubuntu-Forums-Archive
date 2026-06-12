---
title: "Database Locked???  Need some help!"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by thunderstorm on 2006-11-14
*You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.*

I'm using Kubuntu, and this is the message I've been getting this morning with Adept Manager.  My notification icon says there is an update available, but I get this and can't update.  

I did reboot the system, and got the same thing.  I went into system settings and checked the running processes, and only the notification thing was running... which I stopped, but it did not help.

I have nothing else running on any desktop, so I am at a loss.  I'm kinda new to Ubuntu/Kubuntu, so go easy on me if possible.

---

### Post by penguin.ch on 2006-11-14
Thunderstorm,

this sounds to me as if there was a "lock" file (remaining from a recent Adept session or the like) hanging around on your system ... therefore, the console command [COLOR="DarkGreen"]sudo dpkg --configure -a[/COLOR] should help you out of this  stalemate ... ;) 

HTH
Birdy

---

### Post by thunderstorm on 2006-11-14
This thing came up last night, but I had no idea what my architecture is.  I'm using an AMD Semperon processor... but it's not listed there.

---

### Post by dreamszz on 2006-11-24
I had the same error on an AMD64 fresh Kubuntu 6.10 install.
After a huge update, the adept manager had made/encountered an error and couldn't succesfully complete the install/update of 380MB of files.

the cmd reran the post-install configuration and everything was fine.
Thanks for the pointer!

---

### Post by dreamszz on 2006-11-24
> **thunderstorm said:**
> This thing came up last night, but I had no idea what my architecture is.  I'm using an AMD Semperon processor... but it's not listed there.

You are using an x86_64 architecture, BTW. AMD 64 bits.
(good choice!)

---

### Post by dvessels on 2006-12-29
You guys are unbelievable!! Oh, how  I long for the day when I know Linux well enough to provide answers like that instead of constantly seeking them!!!

THANK YOU VERY, VERY MUCH!!!!:o 
dvessels

---

