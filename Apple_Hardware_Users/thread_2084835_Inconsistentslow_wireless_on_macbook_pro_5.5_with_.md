---
title: "Inconsistent/slow wireless on macbook pro 5.5 with 12.10"
date: 2012-11-16
forum: Apple Hardware Users
---

### Post by m038 on 2012-11-16
Hey Guys,

Since i've upgraded from 11.10 to 12.10 i've been experiencing some wireless problems with my Macbook Pro 5.5. 

I installed 12.10 from the CD over my 11.10 installation, only saving /home, rest was formatted. Then i installed the wireless drivers from Software Sources > Additional drivers menu. And voila there was wireless internet.

In general wireless internet works. The first few minutes after a fresh boot or back from hibernate are normal. But then there are hiccups, in which for a few minutes there is almost no connection or it's very slow. I get timeouts on websites and browsing my networkshares is impossible. These problems seem more severe when on battery power, but they do also exist when connected to a power source. (Just to make sure these problems didn't exist in 11.10.)

I've tried using "sudo iwconfig eth1 power off", which should make wireless much faster (at least in 11.10 it did). But it doesn't really seem to have any effect. Even if i monitor wireless speeds in the connection information dialog. (When i check the output of 

I've also tried reinstalling the bcmwl-kernel-source package, hoping it had to do with a kernel upgrade, but no change there.

Here's the output of lspci | grep Network:

03:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

I've been searching for people with similar problems, but i can only find people with driver problems. When i see those instructions they are pretty similar to the step i undertook.

---

