---
title: "firefox slow to load pages on wireless, but works fine on wired lan. help!"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by ijason on 2008-03-16
hey there. 

i'm running 7.10 on a dell inspiron laptop, and firefox has been giving me troubles for a while now. when i'm using the wifi internet other programs seem to run fine; pidgin loads and runs, terminal works fine, ftp runs fine, but firefox either time-outs on page loads, or loads them very VERY slowly. i also get time-outs on system updates. 

when i'm plugged into the wired lan, firefox loads pages just fine.

clearly something is messed up on the wifi end of things. i've already disabled IPv6 system-wide, and the pages resolve quickly... just time-out on the load. there are a half-dozen other computers using the same router, and they all work fine so that eliminates the router as the problem. 

any suggestions?

---

### Post by PapaNerd on 2008-03-17
Wireless 802.11(b) and 802.11(g) hardware will be slower than 100Mb Ethernet connections, but both will be faster than your WAN connection (unless you are in a large corporate environment with a DS3 or better), so we can probably rule out generic differences in the type of connection.

Suggest you check to see that both wired and wireless interfaces are set to the same subnet mask and gateway.  Having no gateway address configured on the wireless interface or a mis-matched subnet mask, for example, could give you those type of symptoms.

---

