---
title: "driver and device loaded"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by jerzydirtracer on 2008-02-29
Hi, I am using a linksys wpc54g pci card, I got it working last nite, I went to reboot, and the wireless dissapered. When it did work, I had all of the networks listed in my area, I did not change anything after boot.Currently ndiswrapper and the admin wireless drivers program lists the driver as valid and device avail. Also in the network tools there was the loopback, eth0, and another eth0 or eth1, I cant remember, but when the three was listed, wireless worked. Now there is just loopback and eth0. Is there a module where the eth0 or eth1 is loaded? Is there a "gedit" command that might have not loaded upon boot?
I was so happy to get wireless and now I do not know what command I typed to get it. 

Thanks
Bob

---

### Post by Whiffle on 2008-02-29
Do 

lsmod


Is ndiswrapper loaded?


While you're at it, how about ifconfig and iwconfig

---

### Post by jerzydirtracer on 2008-02-29
I think I found something. I enabled the restricted driver for the broadcom card. Is this safe? I now have wireless again.

---

### Post by Whiffle on 2008-02-29
Its safe, although those broadcom wireless cards can be pretty picky.  good luck! :D

---

### Post by jerzydirtracer on 2008-02-29
Thanks. I rebooted and I have wireless, matter of fact I am on it now!

---

