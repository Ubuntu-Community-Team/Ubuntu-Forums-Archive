---
title: "CSA trouble"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by CrashintoDMB on 2007-08-23
> **NickArgyle said:**
> I know that this is a pretty old post now, but I was just having this problem with my schools new wireless network, and I did get it to work after a couple of days.

**first you have to configure your settings in Firefox to connect through manual proxy. Input the proxy info and select the check box to apply it to all boxes.**

then, after you download csa.sh, move it to / while running nautilus as root. chmod +x it and run in terminal. It should work now, the main thing is to have csa.sh in tthe root directory (/) and firefox will only be able to connect through the proxy if you manually configure it. 
I still occasionally get an error in Firefox stating "proxy is refusing connections" but to fix this I usually just restart my wireless connection.
You can configure Thunderbird to work as well if you school or college has email by checking what server they are using, and most likely using the same proxy info as in firefox.

Hope this helps people in the future.

I need to know how to do this. 

To anyone who has also had to install the same CSA program, I would really appreciate some help, because i have no idea what im doing (ever).

---

