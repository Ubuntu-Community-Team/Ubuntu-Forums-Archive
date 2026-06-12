---
title: "RWIN setting"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by ron999 on 2006-11-23
Hi
When I use [www.speedguide.net](www.speedguide.net) it tells me:-

******
Default TCP Receive Window (RWIN) = 5840
RWIN Scaling (RFC1323) = 2 bits (scale factor of 4)
Unscaled TCP Receive Window = 1460

**RWIN seems to be set to a very small number. If you're on a broadband connection, consider using a larger value.**
RWIN is a multiple of MSS
Other RWIN values that might work well with your current MTU/MSS:
513920 (MSS x 44 * scale factor of 8)
256960 (MSS x 44 * scale factor of 4)
128480 (MSS x 44 * scale factor of 2)
 64240 (MSS x 44)
******


This is the compact version of the results:-

******
« SpeedGuide.net TCP Analyzer Results » 
Tested on: 11.23.2006 18:02 
Partial IP: 81.97.xxx.xxx 
 
TCP options string: 020405b40402080a0001d1e20000000001030302 
MSS: 1460 
MTU: 1500 
TCP Window: 5840 (multiple of MSS) 
RWIN Scaling: 2 
Unscaled RWIN : 1460 
Reccomended RWINs: 64240, 128480, 256960, 513920 
BDP (200ms): 234kbps (29KBytes/s)
BDP (500ms): 93kbps (12KBytes/s) 
MTU Discovery: ON 
TTL: 53 
Timestamps: ON 
SACKs: ON 
IP ToS: 00000000
******

I am using a broadband connection (2Mbps cable)
what I'd like to know is:-

1) How do I adjust the RWIN setting?
2) What value should I set it to?
:-k

---

### Post by ron999 on 2006-11-25
Bump :rolleyes:

---

### Post by ron999 on 2006-11-27
Bumpity bump :(

---

### Post by flyingbrass on 2006-12-01
The test on the site you linked also says my RWIN is too small.  The [tweak test at dslreports.com](http://www.dslreports.com/tweaks) indicates it's too big.

See [http://www.santa-li.com/linuxonbb.html](http://www.santa-li.com/linuxonbb.html), which explains RWIN test results:

> Now that the window size has been somewhat explained, there are two things that need to be pointed out.   First, most of the web-based bandwidth testers will not correctly assess your windows size.   They usually show the size of the window that they first received, and do not take into account auto-tuning--this is probably because they are written by Windows Users for Windows Users.   And, second, Linux only supports window sizes of up to 64 KB (or 65536 bytes) without enabling window scaling (See rfc1323 "TCP Extensions for High Performance" for additional info on this).

As for changing settings, see [this post](http://www.ubuntuforums.org/showthread.php?p=581296#post581296).  I haven't a clue if those settings are ideal for my situation (7 Mb/s connection) or yours, but after applying them I hit some new personal records in speed test averages.

FWIW, I'm running Dapper with the 686 kernel.

---

### Post by ron999 on 2006-12-01
Thanks for your reply flyingbrass.
It's 1.25am and I'm off to bed so I'll check it out later.
8)

---

### Post by flyingbrass on 2006-12-01
As an aside, your repeated bumps didn't inspire my response.  I searched here on "RWIN" and found the same info you could have.  Your post turned up in the process.

Searching often turns up answers or at least pointers to more information.  It's better to continue searching than give up and bump and beg.  No offense intended.

---

### Post by ron999 on 2006-12-02
Hi flyingbrass
How did you adjust your RWIN setting?

---

### Post by flyingbrass on 2006-12-02
I didn't change my default RWIN.  The settings I altered are in the post linked above.  I added them to the bottom of /etc/sysctl.conf and then to apply the changes I typed:

sudo sysctl -p

---

