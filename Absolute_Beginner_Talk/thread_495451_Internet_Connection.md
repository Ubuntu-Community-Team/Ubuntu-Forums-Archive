---
title: "Internet Connection"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Cullen on 2007-07-08
I have several computers operating on a network.

Tonight I finally configured one of them to be able to view the samba shares on the other. In doing so somehow I disabled this machine's ability to connect to the internet.  It can view network computers and files but not external internet sites, any suggestions?

---

### Post by FleetAdmiral74 on 2007-07-09
The first thing that pops to mind is disable Samba and see if your internet comes back.

---

### Post by HereInOz on 2007-07-09
First up, you need to check your Internet connectivity.

Open a terminal and type:

ping 64.233.187.99

If you get a response then you have basic internet connectivity.  If not, then no internet connectivity.

Then try:

ping google.com

If that doesn't work, but the previous "ping" did, then for some reason you have no DNS resolution.

If they both work, then the only thing I can think of is to open Firefox and type:

about:config

in the address bar and disable IPv6.

---

