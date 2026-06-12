---
title: "X server now disbaled"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by Tucatts on 2006-08-23
Have had Ubuntu installed and running perfectly since June. This morning it failed th boot. I get a window that says "failed to start the X server, maybe not set up correctly. Then asks if I want to view more detail. Says module loader present and a lot of other info. I hit ok a couple more times and it says that X server is now diabled- restart GDM when it is configured correctly. Then goes into dos mode and on the command line for my log on I type my login name, then my password but it keeps telling me I have the incorrect login name. I am putting the correct name I have used with this set up. So there I sit. Any help would be appreciated. Would rather fix this than just reinstall if possible.
Thanks,
Tucatts

---

### Post by 505 on 2006-08-23
The announcement that the latest X update is not working is on the main page of the forums. See [here](http://www.ubuntuforums.org/showthread.php?t=241254). Or you could have used the search function...

Quick fix, log in to the terminal, type 'sudo apt-get update' [enter] then 'sudo apt-get upgrade' It should install a new version of X (10.4) and everything is fine.

---

### Post by Major_Stitch on 2006-08-23
Have you read[This thread]("http://www.ubuntuforums.org/showthread.php?t=241350")?
There are the instructions. As for the login name, it is the one you use when entering your username in GDM (or KDM for KUbuntu). Be sure to have the CAPSLock off and that you didn't misspell your password. Hope it helps!

---

### Post by Tucatts on 2006-08-23
> **505 said:**
> The announcement that the latest X update is not working is on the main page of the forums. See [here](http://www.ubuntuforums.org/showthread.php?t=241254). Or you could have used the search function...

Quick fix, log in to the terminal, type 'sudo apt-get update' [enter] then 'sudo apt-get upgrade' It should install a new version of X (10.4) and everything is fine.
 
505, many thanks, worked like a charm and am up and running. Looked on Ubuntu dapper and found the command line to restart gdm. it is sudo /etc/init.d/gdm restart and all was fine. 

Have a great day!
Tucatts

---

