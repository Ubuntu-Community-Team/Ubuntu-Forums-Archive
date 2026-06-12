---
title: "no internet?"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by not_yet on 2007-07-04
hello all,

I have a windose box and fiesty fawn on my network

this is coming from windose, so connection is good

from fawn, ping is ok to [www.yahoo.com](www.yahoo.com)

problem is browser and email will not connect (firefox / t-bird)

suggestions

thx:D

---

### Post by jasonlfunk on 2007-07-05
What happens if you ```
 telnet www.yahoo.com 80 
```? If you get a connection refused it is probably a router or firewall, but that seems silly. Most likely it's a firewall blocking firefox/tbird. But I dunno.

---

### Post by Seisen on 2007-07-05
Check your settings in Firefox and Thunderbird

Firefox:Edit>Preferences>Advanced>Network Tab>Click on Settings under Connection
Thunderbird: :Edit>Preferences>Advanced>Network Tab>Click on Settings under Connection

---

