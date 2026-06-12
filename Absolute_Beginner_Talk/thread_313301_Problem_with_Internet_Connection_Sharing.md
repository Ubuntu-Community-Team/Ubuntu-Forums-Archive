---
title: "Problem with Internet Connection Sharing"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by UnknownVariable on 2006-12-05
[SIZE="1"]I've got a wireless router in the basement. In my room I have my main computer, a laptop, and just recently another desktop computer. I've set up internet connection sharing and set correct domains / values / etc on my laptop computer. The internet works just fine on it.

I then install a fresh copy of Ubuntu 6.06 on the new desktop and attempt to put the same settings as the laptop has, but I'm only getting a partial internet connection.

By Partial, I mean that I can connect to my router on it (using 192.168.1.1) but I can't connect to any websites in a browser, or download any lists or whatever from URLs.

Any idea as to what could be causing this?[/SIZE]




Silly me, I found a terminal command that fixed it up. I used **sudo dhclient** and magically it started working! :lol:

---

