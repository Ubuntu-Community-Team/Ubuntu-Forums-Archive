---
title: "Asus X55A again"
date: 2013-05-14
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Data 1 on 2013-05-14
A customer sent me one of these still in the box, wanted Ubuntu. I use Ubuntu on plenty of devices and told her I wouldn't have a problem.

Over my head now!

Anyhow I loaded 12.04, no wireless or ethernet of course so I put a USB wireless on it just to do research and try to download some sort of driver. Couldn't figure it out.
I loaded 13.04 and it sees the wireless, sees the wireless networks but won't let me log in to any of them.

According to this article there is a manufacturer version of Ubuntu that works but I can't find any info on it.
[http://www.ubuntu.com/certification/hardware/201206-11376/](http://www.ubuntu.com/certification/hardware/201206-11376/)

So what I would like to know please is the image spoken of in the article available for download anywhere?
Or is there a work around short of a USB or card adapter?

Interesting, I got it to boot from a DVD but was not able to figure out how to get it to boot from USB, had not installed from a DVD in a while.

Thanks-

Jim

---

### Post by Data 1 on 2013-05-19
So nobody else in the world is having this problem but me?

---

### Post by China Diapers on 2013-05-29
> **Data 1 said:**
> So nobody else in the world is having this problem but me?

I'm having similar problems with my Asus X55C. If you look in the wireless forums you'll see hundreds of "wireless not working posts" unanswered.  

I wonder if we would have better luck with another distro? Notebook is not much good without internet.

---

### Post by Data 1 on 2013-06-06
Something must have changed, every post I see on this issue claims it works fine in 13.04 and it simply doesn't. The chipset must have evolved. Since Ubuntu has better support for common devices than any other distro I doubt if switching is a good idea.

lshw -C network shows it as a RT3290 Wireless 802.11n 1T/1R PCIe but says the driver is rt2800pci version 3.8.0-19-generic

I might stumble across a fix, if I do I will be sure to post it here.

---

### Post by China Diapers on 2013-06-07
I got mine working with a Ralink rt5390 wireless, took some tinkering but it's working great now. [h=1][/h]

---

### Post by Data 1 on 2013-06-08
OK... does yours actually have a rt5390 or is that just the driver you used?

---

### Post by Data 1 on 2013-06-15
WOOHOO whatever the latest update was cured this problem 100%, thank you thank you thank you.

---

