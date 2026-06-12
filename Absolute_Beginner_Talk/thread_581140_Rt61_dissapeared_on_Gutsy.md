---
title: "Rt61 dissapeared on Gutsy?"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by BrendanM on 2007-10-19
So I had my rt61 card working fine on Feisty with the legacy rt61 module. Now, when I upgraded to Gutsy, all of the sudden I have no wireless card (it doesn't appear in ifconfig) and if I try to do a "modprobe rt61" I get a "FATAL: Module not found" error. I'm really baffled because other people are reporting this chipset works "out of the box" for them. Is there a way I could get some of that automagic goodness? Is there a way to tell Ubuntu to go get extra driver modules?

Failing that, could somebody post instructions for me on how to download, compile, and install the nightly CVS build of the rt61 module from the serial monkey website? [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)

---

### Post by BrendanM on 2007-10-19
Solved-ish. I was able to download, compile and install the drivers I needed by following the instructions here: [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61)

The fact remains that this shouldn't be an issue anymore. The Rt61 card has been lousy since at least Ubuntu 6.06, but the open source drivers are coming along nicely. Why doesn't this "just work" yet? Do you think it's worth filing a bug report for?

---

### Post by Jadd on 2007-10-19
Why not? Just make sure some one hasn't already reported that bug.

---

