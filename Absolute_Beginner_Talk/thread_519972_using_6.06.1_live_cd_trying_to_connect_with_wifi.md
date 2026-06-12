---
title: "using 6.06.1 live cd trying to connect with wifi"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by MrPhen on 2007-08-07
can someone please give me some instructions on how to get the wifi to work please? :confused:

---

### Post by reckless2k2 on 2007-08-07
you'll need to give some more info than that. open the terminal and type this:

lspci -v 

post the results.

---

### Post by MrPhen on 2007-08-07
> **reckless2k2 said:**
> you'll need to give some more info than that. open the terminal and type this:

lspci -v 

post the results.

ok it gave me a lot of stuff but here's what is said last:

Network controller: Intel Corporation: unknown device 4222 (rev 02)
Subsystem: Intel Corporation: device
Flags: bus master, fast devsel, latency 0, IRQ 169
Memory at efceff000 (32-bit, non-prefetchable) [size=4k]
Capabilities: <available only to root>

---

### Post by MrPhen on 2007-08-07
also i'm a noob so please don't laugh but the only way i know how to open the terminal is ALT + CTRL + F1, but I've seen some screen shots with people having terminal open on the desktop, how do i do that? :|

---

### Post by MrPhen on 2007-08-07
By the way I have a "Intel PRO/Wireless 3945ABG Network Connection".
And I am not using 7.04 because I have the problem with xserver and 6.06.1 does not give me that problem.

---

### Post by overdrank on 2007-08-07
> **MrPhen said:**
> By the way I have a "Intel PRO/Wireless 3945ABG Network Connection".
And I am not using 7.04 because I have the problem with xserver and 6.06.1 does not give me that problem.

HI I see you were not able to solve your graphics issue and I hate to be the one to bring you the bad new but if you search for that wireless card Intel PRO/Wireless 3945ABG it seems to not be good news. :(

---

### Post by MrPhen on 2007-08-07
> **MrPhen said:**
> ok it gave me a lot of stuff but here's what is said last:

Network controller: Intel Corporation: unknown device 4222 (rev 02)
Subsystem: Intel Corporation: device
Flags: bus master, fast devsel, latency 0, IRQ 169
Memory at efceff000 (32-bit, non-prefetchable) [size=4k]
Capabilities: <available only to root>

> **MrPhen said:**
> also i'm a noob so please don't laugh but the only way i know how to open the terminal is ALT + CTRL + F1, but I've seen some screen shots with people having terminal open on the desktop, how do i do that? :|

> **overdrank said:**
> HI I see you were not able to solve your graphics issue and I hate to be the one to bring you the bad new but if you search for that wireless card Intel PRO/Wireless 3945ABG it seems to not be good news. :(

but i went [_here_]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel") and it said it was supported :confused:

---

### Post by MrPhen on 2007-08-07
i think ubuntu just hates me -_-

---

### Post by anewguy on 2007-08-08
First the easy answer:  to get to a terminal  just click on "Applications" scroll down to "Accessories" and then over to and click on "Terminal".

For your wireless, have you looked into ndiswrapper and using the Windows drivers?

---

