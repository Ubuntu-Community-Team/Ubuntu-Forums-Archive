---
title: "Enabling wifi macbook air 10.04"
date: 2010-07-01
forum: Apple Hardware Users
---

### Post by guy m on 2010-07-01
Hi. 

I have installed 10.04 on my macbook air. As I can't physically connect a macbook air to the internet there is no way to download the necessary drivers and the 'hardware packages' doesn't have the nvidea or broadcom packages which were present when I booted off the livecd. I presume therefore that, like gparted, these are only present on the livecd & aren't installed by default. 

When I installed karmic I downloaded the drivers from my mac partition then transferred them over. I've tried doing the same with the lucid equivalents,

[http://packages.ubuntu.com/lucid/patch]("http://packages.ubuntu.com/lucid/patch")
[http://packages.ubuntu.com/lucid/dkms]("http://packages.ubuntu.com/lucid/dkms")
[http://packages.ubuntu.com/lucid/bcmwl-kernel-source]("http://packages.ubuntu.com/lucid/bcmwl-kernel-source")

but when I try to unpack them (32-bit versions as is the version of Lucid I have) in the correct order each returns an error saying the drivers are either damaged or I don't have permission. I definately have the necessary read/write permissions so assume they must be damaged somehow.

If I can't connect to the internet Ubuntu is useless. Has anyone got any idea as to how I can enable wifi please?

---

### Post by domzals1 on 2010-07-03
Wireless can definitely be a bitch. Can you get on the internet in your ubuntu partition via a wired connection?

---

### Post by Tylerjd on 2010-07-03
> **domzals1 said:**
> Wireless can definitely be a bitch. Can you get on the internet in your ubuntu partition via a wired connection?
He wouldn't be able to on a MacBook Air, w/o a wired adapter, as the MacBook Air has no built in Ethernet. 

I would suggest looking for a cheepy USB to Etherent adapter or using Apple's ([http://store.apple.com/us/product/MB442Z/A?fnode=MTY1NDEyMQ&mco=MTA4NzI5MTg](http://store.apple.com/us/product/MB442Z/A?fnode=MTY1NDEyMQ&mco=MTA4NzI5MTg)) to connect your Macbook Air to the Internet, then do as said in the instructions.

---

### Post by domzals1 on 2010-07-04
Good call, totally forgot about that.

---

### Post by guy m on 2010-07-11
I've managed to get it working using the above three files. For some reason I suddenly couldn't boot into Ubuntu so ended up reinstalling it. After reinstalling I dragged the three files mentioned above over to my linux partitions and much to my surprise they installed perfectly.

---

