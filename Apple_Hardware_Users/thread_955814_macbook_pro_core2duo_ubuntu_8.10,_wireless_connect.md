---
title: "macbook pro core2duo ubuntu 8.10, wireless connection drops constantly"
date: 2008-10-22
forum: Apple Hardware Users
---

### Post by SFauconnier on 2008-10-22
Hello.
So I've installed Intrepid Ibex, but (unlike in 8.04), my wireless connection drops constantly.
Like every 2 minutes to every 10 seconds.

It stays connected to my router, but it lost all connection to the internet and my network for at least half a minute.

I didnt have this problem in 8.04 (where I used the ath9k guidelines from someone else on this forum:
[http://ubuntuforums.org/showpost.php?p=5535562&postcount=3](http://ubuntuforums.org/showpost.php?p=5535562&postcount=3) ).

Anyone else having this issue and/or anyone who knows a fix?

Thanks in advance.

---

### Post by cyberdork33 on 2008-10-22
> **SFauconnier said:**
> Hello.
So I've installed Intrepid Ibex, but (unlike in 8.04), my wireless connection drops constantly.
Like every 2 minutes to every 10 seconds.

It stays connected to my router, but it lost all connection to the internet and my network for at least half a minute.

I didnt have this problem in 8.04 (where I used the ath9k guidelines from someone else on this forum:
[http://ubuntuforums.org/showpost.php?p=5535562&postcount=3](http://ubuntuforums.org/showpost.php?p=5535562&postcount=3) ).

Anyone else having this issue and/or anyone who knows a fix?

Thanks in advance.
What driver are you using now?

---

### Post by SFauconnier on 2008-10-23
the one that comes with 8.10 out of the box.
is there any way to look it up?

---

### Post by jizo on 2008-10-23
What brand is your router?  There are some incompatibilities between the broadcom wifi driver and certain routers.  For example at home I've got a Linksys and I have no problems, but at work I've got a Draytek and I experience the exact problems that you are having.  Unfortunately I haven't found a solution to this yet, (other than switch routers) but I hope broadcom will come out with a new version of the driver that addresses these issues.

---

### Post by jwhendy on 2008-10-23
I just succeeded in getting ath9k to work for my MacBook (not Pro), but in the process of beating my head against a wall, I found out that it was the router encryption. Try going to your router config page (usually something like entering '192.168.0.1' in a browser) and turning off encryption, reconnecting, and seeing if that helps at all.

Definitely not for sure, but perhaps worth a shot? My router was WEP protected and would absolutely not work... I got it working with no security, then found out that WPA2 works with the exact same password. Something's buggy, but at least it works now!

Just a thought...

-John

---

### Post by jnorthr on 2008-10-23
Had something like this yesterday, after setting off all security in the router and each machine, entered router config page and forced a router reset - now all my systems are visible to the router and V.V. Now just need to figure out how to put some security back into this kit 8-}

---

### Post by cyberdork33 on 2008-10-23
This is apparently affecting quite a few people...

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/278190](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/278190)

---

### Post by SFauconnier on 2008-10-24
I have an Apple Airport Express 802.11n, and I can confirm that turning off my security is a work-around.

I'll try and turn on WEP instead of WPA2, or something else, since I don't trust having no security at all. I'll report if it worked or not.

---

### Post by SFauconnier on 2008-10-24
After a reboot, my problems are back. :confused:
Still working without security on my router!

---

### Post by jwhendy on 2008-10-24
Bummer... WPA2 was the ticket for me and WEP did not work. Hmmm...

A temporary solution could be just to not broadcast the signal. I thought about this when I hadn't gotten WPA to work for me. At least the general population won't see the network and I doubt there are that many people using tools to scan for hidden networks (majority = win list available networks, apple pull down airport list) to scan for hidden networks?

Just a thought for a temporary way to hide your router?


-John

---

### Post by UnixOS on 2008-11-03
Alright, i'm not sure if I'm having the same Issue as you guys, but here we go.  My internet seemed to be working on the non-secure networks as you guys have established before.

Some time this weekend though (November 1 or 2nd) this all changed and I started getting drops even on regular networks.  I didn't change anything, I may hove downloaded an "Upgrade" but I don't really know why that would do anything bad.

Up to this point I have been running Ubuntu 8.10 on a Macbook Pro, 2.6GHZ...
Kernel version: 2.6.27 - 7
Uhh I just used the driver that was a proprietary driver under hardware drivers...

---

### Post by xiaoqiangwj on 2008-11-03
I have the same problem too..hope someone can help!

---

### Post by UnixOS on 2008-11-05
Alright, after hours of pain and suffering...i have discovered a solution!
or atleast I think.

What I did was, i downloaded [http://apt.wicd.net/pool/intrepid/extras/wicd_1.5.3_all.deb](http://apt.wicd.net/pool/intrepid/extras/wicd_1.5.3_all.deb)
Then, go into synaptic pacakge manager and do a complete removal of Network-Manager...you will now be offline...

Now, simply click on the wicd package and voila it installs, click on applications internet to go to the network manager and set things up

It has worked like a charm for me so far.

---

### Post by Romu on 2008-11-06
SFauconnier and other,
I did some tests regarding wireless on my Macbook Pro 2G (Atheros AR5008 ), here are the results:

[http://ubuntuforums.org/showthread.php?t=971525]("http://ubuntuforums.org/showthread.php?t=971525")

I hope this helps you

---

### Post by ahusain on 2010-02-10
I can attest that this fix works well. I had the same problem with dropped interweb connection

---

