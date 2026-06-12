---
title: "Ubuntu Virgin needs help"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by Rockhoppers1964 on 2007-08-23
Hi Guys and Girls...

I have installed ver 6.06 of Ubuntu on a clean Dell, it is fitted with a Belkin wireless card connecting, (or tryingy) to a D Link G604T router. Router and internet are fine as 5 other Windows PC's have no issues.

I have set the default connection to the wlan, and in terminal can ping all the other PC's and even browse the shared folders on them through the place link, but can't get out to the internet.....to surf or get mail !

Have tried telnet [www.yahoo.com](www.yahoo.com) 80 but get "unable to connect - Time out" error.

What am i missing.

The router is fine, it has the MAC address for the PC and PC Hex codes are all correct, i can even enter the route control panel from Ubuntu.

HELP PlEASE

Andrew

---

### Post by wieman01 on 2007-08-23
Search for "ipv6"... you need to disable in both in Firefox and globally (in Ubuntu).

_**EDIT:**_
Found a link:

[http://ubuntuforums.org/showthread.php?t=307758]("http://ubuntuforums.org/showthread.php?t=307758")

---

### Post by Rockhoppers1964 on 2007-08-23
Thanks, cured the problem with the internet, but has not helped with the e-mail !

Any other ideas

Andrew

---

### Post by wieman01 on 2007-08-23
> **Rockhoppers1964 said:**
> Thanks, cured the problem with the internet, but has not helped with the e-mail !

Any other ideas

Andrew
How are you trying to get your emails? Telnet normally connect on port 23. If you are behind a router or firewall, you might have to open that port. If Internet is fine now, there is an issue with port forwarding I suppose.

---

### Post by Rockhoppers1964 on 2007-08-23
Just using the software shipped with 6.06....evolution

Thanks again

Andrew

---

### Post by wieman01 on 2007-08-23
> **Rockhoppers1964 said:**
> Just using the software shipped with 6.06....evolution

Thanks again

Andrew
If you are using Yahoo's paid services then you should be able to connect via POP/SMTP. Normal free accounts don't offer that kind of service. But no idea what I can advise here.

---

