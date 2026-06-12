---
title: "Wierd internet issue."
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by onefivesix on 2006-07-29
Hi!

I just installed Ubuntu 6.06 on my Dell Dimension 4550. The specs are as following:

2.4ghz P4
512mb NonECC 333mhz DDR RAM(2x256)
Intergrated 10/100 Network adapter (Intel)
Creative Labs SB Live 5.1
Eicon Diva (Passive) 128k ISDN Modem (XP Only)
128mb ATi Radeon 9700 TX With TV-Out

The box is connected to a Linksys WRT54G router via ethernet.

The problem is that i seem to completly lack any connection through the ethernet.

If I try to ping my router it says "network unreachable" and if i try to ping external adresses it says "unknown host"

The result from "route" is...

[I]audun@Audun:~$ route
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
audun@Audun:~$[/I]

...which does not seem right...?

Would you please give me some assistance? I am completly new to linux :(

---

### Post by Ziox on 2006-07-29
i don't think you card's active...go to system => admin. => network or networking tools and check if your cards active...

---

### Post by onefivesix on 2006-07-29
It says Ethernet Interface Eth0 is active...

---

### Post by Ziox on 2006-07-29
then i can't really help you anymore...i'm not too familiar with network connections and stuff...but to test the "route" command, i diabled by ethernet interface, in which case it would return the exact result as yours. Then after activating it, i would get my ip and all that...so...

---

### Post by s_h_a_d_o_w_s on 2006-07-29
not sure, try

sudo pppoeconf

though i'm now sure it will help, try it.

---

