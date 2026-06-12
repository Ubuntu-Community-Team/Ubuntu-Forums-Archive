---
title: "Network Latency Problem"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by cboo on 2006-01-29
Hello,

I've been encountering a strange problem since I've started using Breezy Badger, I'm not sure if this is something that I'm just overlooking, so hopefully someone out there can give me a hand.

I have a 3com 3c2000 family onboard network adapter that Ubuntu detected automatically and configured without problems right after install though my dsl ethernet connection over DHCP.  However, when using a browser (same results with firefox and opera), some sites tend to have a veeery long delay before loading, while others appear almost instantly.  For example, google will load almost instantaneously, so will some other major sites (yahoo, etc).  However, other similarly major sites (ex. slashdot, digg, etc) will take upto 30 seconds or a minute or so before the page loads (ubuntuforums.org as well ;).  

At first I thought this might have been a problem with the network drivers, but I installed the latest 3com drivers for my NIC model and the problem still remained.  I tried putting in another NIC on eth1 (DLink dfe530 txs) and it too has the same problem.  It mostly seems like my Internet latency is very inconsistent, some sites load instantly, some sites take over a minute.  During short periods of time sites might load fine, other times everything sits waiting for a minute.  Note that this isn't a bandwidth or speed issue, I regularly get over 100K/s for certain types of downloads.  I also dual boot, and it's not a hardware problem because I don't have this problem on windows with either the 3com card or the d-link card.  This isn't an incredibly serious problem since the pages *do* always load eventually, but it's getting really irritating having to wait a minute every time I want to use email, read the news, surf the web, etc etc.

Any suggestions?

---

### Post by dickohead on 2006-01-29
Maybe it's your ISP? Maybe you're using IPv6? Maybe your ethernet port is gigbit?

---

### Post by cboo on 2006-01-29
Thanks for the help!  The problem was ipv6,  I disabled it in firefox and edited the modprobe aliases to remove it and the connection is much faster.  It makes sense now that I realize what happened, but I can't be the only person this has affected.  Shouldn't there be some sort of disable ipv6 under Admin>Networking?

---

