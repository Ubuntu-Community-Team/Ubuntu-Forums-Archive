---
title: "ubuntu 14.10 macbook pro 11.1 battery life"
date: 2015-01-21
forum: Apple Hardware Users
---

### Post by lavy on 2015-01-21
I've installed ubuntu 14.10 on my macbook pro 11.1. Almost everything worked out of the box with the exception of wireless (had some problems with it but now works fine), webcam (it doesn't work) and battery life. Now I don't use the camera on my laptop anyway so it's not a huge issue for me, but the under 2 hours battery life is.
Back to my big problem the battery. I have seen it's a very hot topic and I've tried most of the things I found on the internet like:
 - installed a cpu indicator and set it to power save
 - installed laptop-mode-tools and uninstalled them (they didn't work) after that I installed TLP
 - I've installed a fancontrol - which is good because it keeps the laptop from overheating
 - Installed nvidia driver but I don't have an nvidia card. Yes I checked after install :). So my card is:
$ lspci -vnn | grep VGA -A 12
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0a2e] (rev 09) (prog-if 00 [VGA controller])
Subsystem: Apple Inc ..... Kernel driver in use:i915

After all of that my battery status is like this: I opened the laptop at 85%, and after an hour it is at 50% (and says 1:18 minutes left).

Any ideas?
Tx

---

### Post by frob2 on 2015-01-25
I had similar issues on my MBP 11,1 - in my case it was related to a known kworker bug.  The fix was here:   [http://askubuntu.com/questions/176565/why-does-kworker-cpu-usage-get-so-high](http://askubuntu.com/questions/176565/why-does-kworker-cpu-usage-get-so-high)  After following implementing the fix there, my battery-life estimate went from ~2.5hrs to ~7.5hrs.  The system also ran much cooler :-)  This should probably be added to the MBP 11,1 wiki here:  [https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy)  -frob

---

