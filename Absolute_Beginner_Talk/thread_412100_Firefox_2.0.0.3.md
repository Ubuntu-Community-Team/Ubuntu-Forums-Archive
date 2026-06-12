---
title: "Firefox 2.0.0.3"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by danbrownlow on 2007-04-17
Today I finally decided to update 1.5 to 2.0.0.3 and it is working fine. However, I have just tried to install Flash Plugin and used the Manual install, so I downloaded the ,rpm file, using alien did 
```
sudo alien -k flash...
```
then I installed the resulting .deb and it appeared to work fine, however I restarted the browser and the flash plugin isn't working?
Anyone have any ideas on how I can fix this?
Thanks!!! =]]

---

### Post by H.E. Pennypacker on 2007-04-17
You would not be installing flash via RPM or DEB.  Instead, it would be a lot easier if you used Automatix.  You could also do this manually, but if you are a beginner, Automatix is recommended.

---

### Post by danbrownlow on 2007-04-17
When I tried the manual install there was a tar.gz file or a .rpm, so I decided to use the .rpm and use alien to convert it to a .deb.. I thought that would work ok. 
I prefer doing stuff in terminal, get used to all the commands and what no lol. I'm awkward like that. Where can I get this automatix from, or could you tell me the way to do it manually?
Thanks for the reply btw  =]]

---

### Post by r4ik on 2007-04-17
Alternative may be,

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by danbrownlow on 2007-04-17
Ok, now i'm stuck.. I've tried using automatix.. and both ways on the pyscho cats site.. no luck. I really need flash to work! .. but nothing seems to work.
Help! =]

---

### Post by r4ik on 2007-04-17
Shut down you're browser and try,

sudo aptitude install flashplugin-nonfree

Good luck !

---

