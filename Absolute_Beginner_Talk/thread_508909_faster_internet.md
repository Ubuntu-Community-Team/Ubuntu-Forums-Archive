---
title: "faster internet?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by z3phyr on 2007-07-24
hi there
this might just be a coincidence but i've replaced windows xp wit ubuntu maybe a month ago and my internet got really faster. i'm on a broadband 256k modem. it would usually only download at around 30ks but after installing ubuntu it downloads at speeds up to 250ks. but now its back to normal. i know its still capable of speeds of 250 cause i did a speed test and i can download that fast wit a download manager downloader x by splitting up the file. but i cant stream movies at that speed. i was wondering could it be limited by the system or something, from a update. 
also the reason why i said it might be a coincidence is because my internet got really fast once when i was on xp also. it lasted maybe a month too? so it could just be just the isp company stuffing up?

---

### Post by mikewhatever on 2007-07-24
Looks like Ubuntu had nothing to do with it and your last remark explains it.

Cheers :)

---

### Post by Rocket2DMn on 2007-07-24
Speed depends on a few things:
1) the site your downloading from has to allow you the bandwidth
2) other people on your network or ISP can cause you to slow down if they are chewing up bandwidth
3) windows has an overhead of like 20% or so for bandwidth by default (but can be changed)
4) your ISP is capping speeds and/or varying them based on the amount of traffic and/or time of day

---

### Post by FleetAdmiral74 on 2007-07-24
You can always try disabling IPv6. This does not always work, and might not even apply to your situation (some posters said that it was not your install), but is a good measure none-the-less.

---

### Post by dkaddict on 2007-07-24
ISP 'Bandwidth Shaping/Throttling' the lie of the 'unlimited' broadband sale!

---

### Post by bigfox on 2007-07-24
When an ISP tells you "X Speed guaranteed!"  What they really mean is "We guarantee nothing."

---

### Post by benx009 on 2007-07-24
i did notice a slight overall speed increase w/ my internet when using ubuntu feisty than when using windows xp home (went up by about 3kb/s), so 1-up for linux there:)

---

### Post by lisati on 2007-07-24
> **Rocket2DMn said:**
> Speed depends on a few things:
1) the site your downloading from has to allow you the bandwidth
2) other people on your network or ISP can cause you to slow down if they are chewing up bandwidth
3) windows has an overhead of like 20% or so for bandwidth by default (but can be changed)
4) your ISP is capping speeds and/or varying them based on the amount of traffic and/or time of day

The ISP I use has this to say about speed as well:
[http://jetstream.xtra.co.nz/chm/0,6858,204576-203090,00.html](http://jetstream.xtra.co.nz/chm/0,6858,204576-203090,00.html)

If I think there's a problem, I sometimes check [http://www.consumerspeedtest.org.nz/speedtest.php](http://www.consumerspeedtest.org.nz/speedtest.php)
(you might need a plugin for firefox to use this one correctly)

EDIT: The ISP I use puts a speed cap on the plan I'm on when I exceed my gigabyte limit for the month. They reckon it's dial-up speed. The funny thing is that when they've done it to me, I've still had faster speeds on ADSL then when I was on dial-up, even though I've still got the same rubbishy phone wiring in my house (phone line in from street, with exposed connection to the internal wiring just above my front door, one rather battered phone socket not far from that, plus a bunch of extension leads to get the phone line to where I need it. I'm surprised that my connection goes as well as it does.)

---

### Post by alienexplorers on 2007-07-24
Disabling IPV6 made a difference in my internet speeds.  I disabled it in:> gksudo gedit /etc/modprobe.d/blacklist  I added to the end of the file blacklist IPV6.  I also disabled IPV6 in Firefox by changing the line > user_pref("network.dns.disableIPv6", true);.

---

### Post by Zzl1xndd on 2007-07-24
Its also worth mentioning that there is a large difference between kB and Kb most ISP's messure there speed in Kbs or mbs cause 8Megabits per second sounds a lot better then 960killoBites.

---

### Post by z3phyr on 2007-07-24
but i still get high speeds downloading with downloader x.  the bandwidth seems to be limited by something but downloader x seems to get pass it.  i thought that would be impossible if the isp is limiting the bandwidth

---

