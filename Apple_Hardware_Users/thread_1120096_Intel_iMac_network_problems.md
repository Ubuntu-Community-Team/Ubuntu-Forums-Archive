---
title: "Intel iMac network problems"
date: 2009-04-08
forum: Apple Hardware Users
---

### Post by knattlhuber on 2009-04-08
I am running Hardy on an 2.4GHz Intel iMac (Model 7,1). Today I ran a kernel update and some other updates and before rebooting, my Network monitor suddenly started to continously show some 400kb/s download traffic for some 20 minutes. Then suddenly, I lost my ethernet connection (monitor still showing heavy traffic). I rebooted into the new kernel, but the network wouldn't reconnect. Yet the network monitor still indicated heavy downstream traffic. Rebooted into back into the old kernel, same issue.

Even more odd, I was installing Intrepid on a Pentium IV box at the same time and exactly the same stuff happened on that machine: Network gone, network monitor showing the strange 400kb/s traffic. The iMac and the Pentium IV have different network cards (Marvell Yukon and Intel, resp.)

After not being able to figure out what the problem was, I quickly installed Intrepid on the iMac (retaining the /home partition). Still same problem. Created new user, still same issue.

I had suspected that maybe the router/bridge is going crazy but my coworkers (all on Wintel) have no problem. And, if I boot into the OSX partition on the iMac, the network is working fine.

syslog indicates that the DHCP lease attempt times out but that's all I could see in the logs.

I'm at a total loss about what's happening here. I called IT (this is my work computer), but, of course, they only support Windows XP. Any suggestion where the problem might lie is greatly appreciated.

---

### Post by knattlhuber on 2009-04-09
**ISSUE SOLVED**

Turned out to be a network problem. The Windows computers in our office went offline a couple of hours later.. It just happened that the Linux machines were affected first. Not sure why.
IT restarted the router this morning and now everything's tickly-boo again.

---

