---
title: "Open Ports in Firestarter"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by broth420 on 2007-06-25
I am wondering how I can open up specific ports in firestarter (or IP tables)
my biggest question is the type of port, ie udp or tcp

I need to open up port 3483 udp, 3483 tcp, and 9000 tcp (for slim server), but I don't see this option to pick upd or tcp.  Does it open up both by default when you choose the port number?

---

### Post by NZJon on 2007-07-01
Hi. I don't have an answer, but I am interested in the solution, as I also am trying to open up ports for my SlimServer installation. 

Cheers,
   Jon

---

### Post by HotShotDJ on 2007-07-01
Check out [THIS]("http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html") page -- it may (or may not) be helpful.  Since I don't run Firestarter myself, I can't give you much more information than what I learned from Google.

---

### Post by Seisen on 2007-07-01
Right click where it says Allow service|Port|For in the policy tab and then select add rule and fill in the information as needed.

---

### Post by NZJon on 2007-07-06
Thanks HotShotDJ & Seisen for your replies. It turned out that Firestarter was working correctly--it was my installation of SlimServer that was broken.

The version of SlimServer in the Ubuntu repositories is a couple of years out of date. If anyone else is having problems with not being able to access port 9000 on thier SlimServer, check that you have installed the version from 

deb [http://debian.slimserver.com](http://debian.slimserver.com) stable main

Hope that helps

Jon

---

