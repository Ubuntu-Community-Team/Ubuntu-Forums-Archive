---
title: "ibook jumps from 400mhz to 600 back to 400"
date: 2005-09-27
forum: Apple PPC Users
---

### Post by zenlunatic on 2005-09-27
I installed the CPU frequency scaling monitor applet for gnome and it shows system usually at 400mhz but sometimes it jumps to 600 (my systems max). I am on an ibook. Should I set it to be 600 all the time? If so how do I do that? Thanks.

---

### Post by callipeo on 2005-09-27
The default setup in Ubuntu is to set the frequency to the lowest, then bump it to the highest frequency when the cpu usage goes over 80%, and gradually decrease it to the lowest frequency when the cpu usage goes below 20%. This is good in my opinion, especially on a laptop, and I don't see any reason to use the highest frequency all the time. If you want to tweak the frequency scaling however, you should have a look at the /etc/power/scripts.d/cpufreq file.

---

