---
title: "Boot Problems"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-07-06
Howdy, so when I'm running linux because things shut down so many times recently it does the self test and runs the checker on my hard drive. Unfortunatly it's bouncing back with an error, it says it can run an fdisk and when I input  my root password to do so it doesn't go any farther and logs back to the basic login screen. This is continuous as I cannot move past this everytime I reboot. Any ideas how to get around the hard drive check? Or should I just whipe everything and load up fiesty? I mean before this I had a freakingly great smooth Dapper Drake install going!! :( Let me know! Thanks guys/gals!

---

### Post by overdrank on 2007-07-06
> **Tumpster said:**
> Howdy, so when I'm running linux because things shut down so many times recently it does the self test and runs the checker on my hard drive. Unfortunatly it's bouncing back with an error, it says it can run an fdisk and when I input  my root password to do so it doesn't go any farther and logs back to the basic login screen. This is continuous as I cannot move past this everytime I reboot. Any ideas how to get around the hard drive check? Or should I just whipe everything and load up fiesty? I mean before this I had a freakingly great smooth Dapper Drake install going!! :( Let me know! Thanks guys/gals!

Hi I recently had this happen so try this, 
Alt,ctrl F1 keys all at the same time then login using your user name and password. Then use the command ```
*sudo su*
```  enter your same password and then enter the command 
```
fsck
```
And yes. then you should be ok
Hope this helps good luck!:popcorn:

---

