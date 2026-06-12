---
title: "Configuring Apache with MediaWiki"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by rootleafhmmm on 2006-06-15
Hi EB,
I setup an Ubuntu machine with my Wiki running already,  I learned that by the Mediawiki itself you cannot restrict access into your Wiki, but by configuring/tweak Apache2 you could limit those who access my MediaWiki page. This machine is connected to a local LAN and is connected to the internet. I just wanted a few static IP  addresses to be able to access this machine/MediaWiki/ is there any way for such restriction.

---

### Post by michux on 2006-06-15
[QUOTE=rootleafhmmm]Hi EB,
I setup an Ubuntu machine with my Wiki running already,  I learned that by the Mediawiki itself you cannot restrict access into your Wiki, but by configuring/tweak Apache2 you could limit those who access my MediaWiki page. This machine is connected to a local LAN and is connected to the internet. I just wanted a few static IP  addresses to be able to access this machine/MediaWiki/ is there any way for such restriction.[/QUOTE]

Of course it's configurable. You need to read abot the "Directory" element in the Apache config. You can restrict access to each directory on your web server. The best way seems to be fist deny access to all and then enable it for custom IPs. Seach in Google for "apache restrict access IP" - some nice articles will show up for sure.

---

