---
title: "Can't Load Certain Websites (Kubuntu Gutsy)"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by sunexplodes on 2007-10-25
I'm not sure when this happened, but I've noticed it in the last week or so. I can't seem to access Metafilter.com. Every attempt times out. In every browser (konqueror, firefox, opera). But I can ping it, and Google cache shows that it's been in operation this whole time. 

SO. Is there something I can do to my hosts file? Or another workaround for something like this? I'm using OpenDNS and it worked fine until relatively recently.

---

### Post by ThrobbingBrain66 on 2007-10-25
I'll start with the obvious question and ask if you've removed/disabled OpenDNS to see if that makes any difference.

---

### Post by sunexplodes on 2007-10-25
> **ThrobbingBrain66 said:**
> I'll start with the obvious question and ask if you've removed/disabled OpenDNS to see if that makes any difference.

Yeah, no difference, sadly.

---

### Post by sunexplodes on 2007-10-26
No dice? I assume all YOU guys can see that website just fine? It's just me?

Ideas?

---

### Post by sunexplodes on 2008-01-04
This is STILL happening. Anybody got a clue? 

I can ping it fine, and here's a traceroute:

traceroute to metafilter.com (74.53.68.130), 30 hops max, 40 byte packets
 1  192.168.0.1 (192.168.0.1)  0.352 ms  0.360 ms *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * ge-5-2-110.hsa2.Detroit1.Level3.net (64.152.144.1)  27.191 ms  27.718 ms
 7  ae-8-8.ebr2.Chicago1.Level3.net (4.69.133.242)  37.074 ms  37.301 ms  37.995 ms
 8  ae-78.ebr3.Chicago1.Level3.net (4.69.134.62)  38.727 ms  39.692 ms  39.937 ms
 9  ae-3.ebr2.Denver1.Level3.net (4.69.132.61)  78.149 ms * *
10  ae-1-100.ebr1.Denver1.Level3.net (4.69.132.37)  84.243 ms  84.735 ms  85.002 ms
11  ae-2.ebr2.Dallas1.Level3.net (4.69.132.106)  107.898 ms  108.101 ms  78.235 ms
12  ae-92-92.csw4.Dallas1.Level3.net (4.69.136.150)  82.789 ms  87.345 ms  87.512 ms
13  ae-44-99.car4.Dallas1.Level3.net (4.68.19.198)  87.005 ms  68.369 ms  69.374 ms
14  THE-PLANET.car4.Dallas1.Level3.net (4.71.122.2)  70.354 ms  70.184 ms  70.789 ms
15  te9-2.dsr01.dllstx3.theplanet.com (70.87.253.14)  71.777 ms te7-2.dsr01.dllstx3.theplanet.com (70.87.253.10)  73.716 ms  74.729 ms
16  76.fd.5746.static.theplanet.com (70.87.253.118)  76.846 ms  77.245 ms 7a.fd.5746.static.theplanet.com (70.87.253.122)  79.073 ms
17  po2.car05.dllstx6.theplanet.com (12.96.160.39)  150.460 ms  150.658 ms  151.108 ms
18  82.44.354a.static.theplanet.com (74.53.68.130)  81.960 ms  89.552 ms  94.151 ms
19  82.44.354a.static.theplanet.com (74.53.68.130)  82.646 ms * *

---

### Post by sunexplodes on 2008-01-04
SOLVED

After searching in google for similar problems, I decreased the MTU on my router, and can now access these sites. 

Cheerio.

---

