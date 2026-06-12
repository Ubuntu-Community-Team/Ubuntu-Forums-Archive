---
title: "WLAN Problem."
date: 2005-09-11
forum: Absolute Beginner Talk
---

### Post by lil_penguin on 2005-09-11
Hi! 
Ubuntu has worked fine on my laptop, but i have one problem my [AirConn] INPROCOMM IPN 2220 Wlan card doesnt  work. Anyone encountered same problem? How could i fix it?

---

### Post by sneax on 2005-09-11
I did a small search on internet and it seems you have to make your card work by using ndiswrapper - which uses the windows drivers, wraps around them, and make them usable in linux.

Search for a howto for ndiswrapper!

---

### Post by mlomker on 2005-09-11
It looks like that adapter doesn't have a native linux driver, so you'll need to use ndiswrapper (a tool that lets you install a Windows wireless driver in linux).

[Here's the how-to.](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

---

### Post by lil_penguin on 2005-09-11
thanks, but how do I install the .deb file for ndiswrapper? Apt-get didnt work. 
i know how to extract .deb to my desktop but how do i install it?

---

### Post by lil_penguin on 2005-09-11
Nevermind, readed the guide till end and understood it all, though, theres little problem: I Dont know where i could get drivers for my wlan card, google didnt help me.

---

