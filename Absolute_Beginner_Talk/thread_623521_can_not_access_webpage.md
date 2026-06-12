---
title: "can not access webpage"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by wolkengold on 2007-11-25
Hello,
I have the problem to call the webpage strato.de from costa rica.
Whether I use firefox or lynx I get a time out. The nameservers run well. I get an IP-Adress.
If I do a tracepath I recognize that it is more than 30 hops to reach the webpage.
The webpage strato-hosting.co.uk is reachable after 28 hops.
My question is how to configure more than 30 hops?
Any Ideas?

Here is the tracepath.
soarcs@orlov:~$ tracepath strato.de
 1:  orlov (192.168.2.102)                                  0.404ms pmtu 1500
 1:  DD-WRT (192.168.2.1)                                   4.571ms 
 2:  10.10.0.1 (10.10.0.1)                                 47.077ms 
 3:  10.10.0.250 (10.10.0.250)                            asymm  2  81.855ms 
 4:  no reply
 5:  10.82.65.65 (10.82.65.65)                            asymm  4 100.829ms 
 6:  200.91.109.9 (200.91.109.9)                          asymm 10 103.260ms 
 7:  200.9.48.213 (200.9.48.213)                          asymm  8 110.861ms 
 8:  sl-st20-mia-5-2.sprintlink.net (144.223.247.113)     144.504ms 
 9:  sl-bb21-mia-12-0-0.sprintlink.net (144.232.2.196)    asymm  8 140.352ms 
10:  sl-bb20-dc-14-0-0.sprintlink.net (144.232.9.25)      asymm  9 160.680ms 
11:  sl-bb26-rly-6-0.sprintlink.net (144.232.20.13)       asymm 10 198.041ms 
12:  sl-bb27-rly-13-0.sprintlink.net (144.232.14.182)     asymm 11 162.712ms 
13:  sl-bb22-pen-13-0.sprintlink.net (144.232.18.187)     167.122ms 
14:  sl-bb27-pen-9-0.sprintlink.net (144.232.16.54)       asymm 12 167.216ms 
15:  sl-bb21-nyc-2-0.sprintlink.net (144.232.20.96)       asymm 16 171.346ms 
16:  sl-gw37-nyc-0-0-0.sprintlink.net (144.232.13.64)     174.843ms 
17:  sl-btglo1-137998-0.sprintlink.net (160.81.101.86)    asymm 12 168.214ms 
18:  t2c2-p5-0-0.uk-ilf.eu.bt.net (166.49.164.62)         asymm 13 286.247ms 
19:  t2c2-p8-0.uk-lon2.eu.bt.net (166.49.195.126)         asymm 14 262.971ms 
20:  t2c2-p1-0.nl-ams2.eu.bt.net (166.49.208.129)         asymm 15 269.980ms 
21:  t2c2-p4-0.de-dus.eu.bt.net (166.49.195.50)           asymm 19 278.086ms 
22:  t2c2-p2-0.de-fra.eu.bt.net (166.49.195.158)          asymm 18 282.056ms 
23:  t2a5-ge6-1.de-fra.eu.bt.net (166.49.172.124)         asymm 18 282.227ms 
24:  166-49-148-246.eu.bt.net (166.49.148.246)            asymm 17 275.888ms 
25:  so-0-0-0-0.ffm4-j.mcbone.net (62.104.200.154)        asymm 17 277.058ms 
26:  L0.kar2-g.mcbone.net (62.104.191.137)                asymm 17 282.835ms 
27:  strato-kar1.fdknet.de (194.97.172.186)               asymm 15 267.949ms 
28:  81.169.146.66 (81.169.146.66)                        asymm 17 283.174ms 
29:  no reply
30:  no reply
31:  no reply
     Too many hops: pmtu 1500
     Resume: pmtu 1500

---

### Post by fenixphire07 on 2007-11-26
hey..**** i forgot ur name, sorry. Anyway, i dnt think increasing the hops is the problem coz by 28 its already not responding. and 29 and 30 are simply trying to reestablish the connection - hence it requires to repeat 1 to 28. Also increasing the hop will affect your internet performance. 

So consider finding an alternate site. Or a redirect from some site to the site you wish to visit directly

: I'm not an expert but i hope this helps. :

---

