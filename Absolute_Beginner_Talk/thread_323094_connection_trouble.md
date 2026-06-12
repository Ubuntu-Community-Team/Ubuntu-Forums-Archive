---
title: "connection trouble"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2006-12-21
i have a pppoe connection which works fine but...i have to set it up (and i mean go through "sudo pppoeconf" ) every time i boot or otherwise it won't work. any suggestions?
i'd be thankful as this is banging my nerves already :) !

---

### Post by EminNew on 2006-12-21
In pppoeconf, try answering "no" when asked if you want to connect automatically on boot.

Then use "pon dsl-provider" to connect, "plog" to check if you're connected, "poff" to disconnect.

Some people have to pon and poff a couple of times before they successfully connect.

Or you can try to delete DNS entries in "Administration -> Networking" and then using pon to connect. I don't know why, but sometimes this works for me.

---

