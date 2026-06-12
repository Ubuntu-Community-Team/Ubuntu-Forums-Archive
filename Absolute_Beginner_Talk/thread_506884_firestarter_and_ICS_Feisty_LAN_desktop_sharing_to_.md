---
title: "firestarter and ICS: Feisty LAN desktop sharing to XP wireless laptop"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Adahn on 2007-07-22
the suspects:
Desktop Feisty connected to wired router, USB wirelessG adapter
WAN settings in feisty: local zero conf network (ive tried dhcp)

winXPsp2 laptop with integrated wireless, set to aquire any network

Laptop is getting connection signal (5 bars), but not internet 


Network settings in Feisty list a second wireless device : (wmaster0) with the same available settings as wlan0.

when trying  firestarter (to link LAN to either wlan0 or wmaster0) I get an error, 'device not ready'.

---

### Post by weblordpepe on 2007-07-22
Sounds like an issue with Firestarter. To be honest. You don't need it. The desktop-firewall concept is only really valid on Windows, in my opinion.

Its a bit of a throwback from the Windows world that security be managed by something other than the OS. Just uninstall firestarter. All it is really is a front-end for kernel options. 

In Windows a desktop firewall would help stop trojans doing stuff (in theory). In Linux, all it does is annoy you & make stuff not work right.

---

### Post by Adahn on 2007-07-22
I thought firestarter was needed to share the connection.

I exited firestarter and still no joy.

---

