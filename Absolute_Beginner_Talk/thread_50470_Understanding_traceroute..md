---
title: "Understanding traceroute."
date: 2005-07-20
forum: Absolute Beginner Talk
---

### Post by bk452 on 2005-07-20
I ran traceroute and this is the output:

traceroute [www.ubuntuforums.org](www.ubuntuforums.org)
traceroute to ubuntuforums.org (64.21.33.9), 30 hops max, 38 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *


what does this mean?

---

### Post by MikeyXX on 2005-07-20
[QUOTE=bk452]I ran traceroute and this is the output:

traceroute [www.ubuntuforums.org](www.ubuntuforums.org)
traceroute to ubuntuforums.org (64.21.33.9), 30 hops max, 38 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *


what does this mean?[/QUOTE]
 Means there are no responses from your machine to your target. So I'd be saying that your network card isn't functioning...but then again you are on the net so that's wierd.

---

### Post by Juergen on 2005-07-20
It usually means that a particular router has been configured to drop ICMP packets (pings) rather than respond to them.

Maybe your cable/dsl-modem has such a setting?

---

### Post by bk452 on 2005-07-20
Thanks.  I'll check out the modem.

---

### Post by bk452 on 2005-07-20
[QUOTE=MikeyXX]Means there are no responses from your machine to your target. So I'd be saying that your network card isn't functioning...but then again you are on the net so that's wierd.[/QUOTE]
 Means there are no responses from your machine to your target.***

I was going to chuck it off as a useless app, but I'll try to figure it out.

---

### Post by Kvark on 2005-07-20
I lose the trace to ubuntuforums.org too. But I lose it after 15 hops instead of on the first one.

Would copy paste the result to here but can't figure out how to copy from the network tools window.

---

### Post by KrIaXPaTaLa on 2006-01-25
I cant traceroute any address, neither on my desktop or my laptop (same dist, breezy 5.10, traceroute grabbed with apt-get, but I can traceroute anything in windows xp without any problem (same laptop (dual boot)). Is there that mutch difference between win and nix in this app? I've enabled ping reply on my router, but still got no better result. Any thoughts?

Best regards,

KrIaX.

---

