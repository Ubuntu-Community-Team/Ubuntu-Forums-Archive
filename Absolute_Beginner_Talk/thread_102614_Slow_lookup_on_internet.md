---
title: "Slow lookup on internet"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2005-12-12
My ubuntu machine seems to take ages to look up and transfer data from websites. Im on a 10Mb line and have no probs on my windows machine. Im running gnome  and breezy distro (dont know how to get the version :???: ).
I remember ages ago i read something about breezy and internet slowness, and how to get it optimal but cant find it again.

Any ideas

---

### Post by canadianwriterman on 2005-12-12
If you are using Firefox, type **about:config **in the URL address bar. Then search for **network.dns**. Find the line with **ipv6** in it, and double click it to change the default to **true**. That should help.

---

### Post by ardchoille on 2005-12-12
**Obtaining more speed from Firefox**

This will help you make firefox load pages a little faster than usual:

   1. Open firefox
   2. Go to the address bar and enter: about:config hit enter
   3. Go to the filter box Filter Box
   4. In filter box go to: network.dns.disableIPv6 double click to change it to be: true
   5. In filter box go to: network.http.pipelining double click to change it to be: true
   6. In filter box go to: network.http.pipelining.maxrequests double click it to change from 4 to 8 click OK.
   7. In filter box go to: network.http.proxy.pipelining double click to change it to be: true
   8. Restart firefox! 

More tips and tricks for tweaking Firefox can be found here: [http://www.mozilla.org/support/firefox/tips](http://www.mozilla.org/support/firefox/tips)

Hope this helps

---

### Post by Mission 10 on 2005-12-14
Yes, those tweeks really speed it up. But I have some additional ones that can help out also.

network.http.max-connections : 64
network.http.max-connections-per-server : 21

And for our poor friends with dial-up...

browser.cache.disk_cache_ssl : true
browser.xul.error_pages.enabled : true
content.interrupt.parsing : true
content.max.tokenizing.time : 3000000
content.maxtextrun : 8191
content.notify.backoffcount : 5
content.notify.interval : 750000
content.notify.ontimer : true
content.switch.threshold : 750000
network.http.max-connections : 32
network.http.max-connections-per-server : 8
network.http.max-persistent-connections-per-proxy : 8
network.http.max-persistent-connections-per-server : 4
network.http.pipelining : true
network.http.pipelining.maxrequests : 8
network.http.proxy.pipelining : true
nglayout.initialpaint.delay : 750
plugin.expose_full_path : true
signed.applets.codebase_principal_support : true

[IMG]http://i25.photobucket.com/albums/c93/jlindfors/sigpic2copy.gif[/IMG]

---

