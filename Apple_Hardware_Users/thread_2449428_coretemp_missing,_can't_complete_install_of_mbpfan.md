---
title: "coretemp missing, can't complete install of mbpfan on early 2006 MacBook Pro (18.04)"
date: 2020-08-26
forum: Apple Hardware Users
---

### Post by danish-bronco on 2020-08-26
Hi everyone, 

The title pretty much sums it up: I'm trying to complete the install of mbpfan on my early 2006 MacBook Pro after successfully installing and updating/upgrading Xubuntu 18.04 (32-bit) in a dual-boot with Snow Leopard, but when I'm trying to start mbpfan, I get an error in Terminal stating that coretemp is missing. 

I modified the /boot/loader.conf file and added the coretemp line, rebooted, but still a no-show on coretemp's part. 

Xsensors returns temps and fan revs thanks to apple smc, but i should also see a coretemp tab in the xsensors window, and it's nowhere to be found. 

Is there a way to download/install coretemp manually, then run it? I'd like to avoid reinstalling Xubuntu, if it's possible. 

This Mac is prone to overheating, so a little help would be much appreciated!

EDIT: Apparently, the problem solved itself after updating and upgrading Xubuntu. I can now see the coretemp tab in Xsensors, and sure enough, mbpfan works as it's supposed to. Go figure.

---

### Post by howefield on 2020-08-26
Thread moved to the "*Apple Hardware Users*" forum.

---

