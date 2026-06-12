---
title: "wifi card working but cannot connect to the network"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by neil85ae86 on 2007-06-01
I only have a wifi connectivity on the edubuntu machine I'm building for my 7 year old to play with, so please exscuse the lack of screenshots and copy and pasting.

I've installed my wifi card without any serious issues, it's an unsupported one but I was able to get it installed and seemingly working using ndiswrapper ..but network manager doesn't seem to be controlling it correctly.

The NM icon in the corner will show me as connected to various networks, the signal strenght is good, but the info. in NM doesn't always jive with what in iwconfig.  ie. I'll enter a wep key, but iwconfig will show as encryption off.

I am getting very frustrated.

I've tried DHCP/static/manual/roam ..I cannot get an IP. 

My route table is empty, is this normal?

It seems like not everything required to be networking is fired up.  I've just about exhausted myself googling how-tos etc. and I'm at wits end.

Any help is always appreciated.

Neil

---

### Post by kernel tom on 2007-06-01
I would use wlassistant and run it as root...

if u can download it wired thats the best way

sudo apt-get install wlassistant

then run it as root

sudo wlassistant

when it comes up you can click, configure, and connect to ur wireless network

---

### Post by Aquakidd13 on 2007-06-01
Calm down man lol or woman not sure, But you aren't alone,  I had this happen on Debian with my laptop, Im still looking for an answer, Maybe someone here will :D  I haven't had ant problems with my Ubuntu on my test desktop, I'm still on the move from Windows to Linux ...

---

