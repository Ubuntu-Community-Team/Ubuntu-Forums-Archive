---
title: "Speed up my Wireless connection?"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by neocookie on 2006-08-15
Hi guys

I've been using my wireless connection around the house since I got my laptop, and this morning I used my gf's desktop which is plugged directly into the router. Her connection (on a virus-riddled winxp install and IE6 with no-end of pop-ups) was much faster than my WiFi on a new Dapper install.

Any ideas how I could tweak my settings to get more speed from my wireless card?

---

### Post by tribaal on 2006-08-15
Well something that really changed the world for my config is the following trick (would have put a link to the source, but I can't remember where I got that from...):

1. Open Firefox
2. In the URL bar, type in "about:config" (without the quotes)
3. In the "filter" field (very top of the page), type in "ipv6"
4. There should be a single line left on the page, reading "network.dns.disableIPv6". Double click it so that the value turns to "true".

Restart firefox.

Was *much* faster for me after that.

Hope this helps...

- trib'

---

