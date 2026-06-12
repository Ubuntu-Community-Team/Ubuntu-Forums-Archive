---
title: "New version of Video4Linux - how to install?"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by Darrarski on 2007-02-01
I'm using Ubuntu 6.10 and I have problem with my tv card, exactly with remote controller plugged to this card. I have Pinnacle PCTV 110i with gray-colored rc, I can watch tv with sound using tvtime, only my remote controller not working at all. I read that I have to use saa7134 module with option pinnacle_remote=1, but version of saa7134 in my system, don't have this option supported (there is not on the "modinfo saa7134" list). On the [v4l page]("http://linuxtv.org/downloads/CHANGES") I read that this option, and my rc is better supported with newer version of v4l. So, I need newer version of this module. I downloaded latest version form [this site]("http://linuxtv.org/hg/v4l-dvb?cmd=manifest;manifest=0d31afa1d53e583b629961a93a80b90147c33c04;path=/;style=gitweb"), unpacked to /usr/src/ and done make and make install, but it seems that nothing changed in my system. How can I upgrade v4l in my system? Help me, I'm beginner.

EDIT: Ok, my system needed to be restarted twice and new version working well.

---

