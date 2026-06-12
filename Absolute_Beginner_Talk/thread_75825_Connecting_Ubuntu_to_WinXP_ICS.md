---
title: "Connecting Ubuntu to WinXP ICS"
date: 2005-10-14
forum: Absolute Beginner Talk
---

### Post by eClaW on 2005-10-14
Hello there,

first I want to say that I'm impressed by the community here, there seem to be a lot of helpful people around. :)

Ok, following scenario: I have a

**[WinXP box]** with connection to the internet
and a
**[Ubuntu 5.10 box]** that i want to configure so that it uses the Internet connection from my WinXP box.
They are connected via CrossOver LAN cable.

It is not possible to connect my Ubuntu box directly to the internet.

So I tried setting upWinXP ICS normally, i.e. giving it IP 192.168.0.1 subnet 255.255.255.0. Then in my Ubuntu box i set up networking with IP 192.168.0.4 subnet 255.255.255.0 and gateway 192.168.0.1. --> didn't work.

So I set my Ubuntu box networking to DHCP, but that didn't work either.

If anyone had a solution for this i would be very grateful!!!

regards,
eClaW

---

### Post by Borusa on 2005-10-14
Switch back to defining your IP address manually - 192.168.0.4 should be fine.

Make sure that the XP box is connected to the internet.
Can you open a terminal window (Applications->Accessories->Terminal under Breezy) and try the following

First : 
```
ping 192.168.0.1
```
If that works (returns sensible things...) then Ctrl-C to cancel then

```
ping 216.109.117.206
```
If that works (doesn't come back with repeated error messages) Ctrl-C again then
```
ping www.yahoo.com
```
Let me know how it goes!

---

