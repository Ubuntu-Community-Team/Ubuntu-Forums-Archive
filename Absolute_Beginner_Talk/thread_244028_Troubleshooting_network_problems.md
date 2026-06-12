---
title: "Troubleshooting network problems"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by spyke01 on 2006-08-25
hi guys, i just went thorugh some problems with networking, and i was wondering about what kind of networking tools we have to trouble shoot with.

what are the following in linux for example?(feel free to add others as well)
ipconfig
ipconfig /release
ipconfig /renew
tracert
nbtstat

---

### Post by clapper65 on 2006-08-25
ifconfig - shows interfaces etc
tcpdump - dumps all TCP traffic
tcptrace - reads tcp dump info
ethereal - traffic analyzer

Check the man pages to get all the gory details.

ie. man ifconfig

---

