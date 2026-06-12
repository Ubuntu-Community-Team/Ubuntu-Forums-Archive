---
title: "Windows 7 networking query"
date: 2011-12-28
forum: Any Other OS
---

### Post by dacman48 on 2011-12-28
Im on a windows 7 machine, and yes i realize that this is a linux forum, but io could think of no smarter group on individuals to ask. Lets say that i have 2 connections on this machine, connection A and connection B. Connection A has internet access, connection B doesnt. Frequently, i have devices on both these networks that i need to access through http, ftp, etc. my question is, is there any program i can use to either switch between connection A and B based on the program or a software method to specify the primary connection windows is using? thank you in advance.

---

### Post by dandnsmith on 2011-12-29
As asked, the only method I can think of which will work is to have the network connections each dealing with a different network/subnet.
That way it is possible to set up routes which will direct traffic according to net/subnet, which will get you what you want.

I haven't done this with Win7, but the basics are the same as WinXP - the tricky part is finding them.

If you haven't done any subnetting or routing, you will need to read up a little on the commands available and how they operate - can be tricky for the unaccustomed, so be prepared for trouble and the need to diagnose problems with firewalls and routing.

---

### Post by dacman48 on 2012-01-04
darn, i was hoping for an easy solution. ty anyway derek

---

### Post by mips on 2012-01-05
> **dacman48 said:**
> Lets say that i have 2 connections on this machine, connection A and connection B.

Please define connection A & B. Are they PPPoE connections, do you have dual LAN ports/connections etc etc. I need more information.

In the mean time look at [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/route.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/route.mspx?mfr=true)

---

