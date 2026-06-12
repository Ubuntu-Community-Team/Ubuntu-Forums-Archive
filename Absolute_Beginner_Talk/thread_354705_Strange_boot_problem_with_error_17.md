---
title: "Strange boot problem with error 17"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2007-02-06
Hi all! I have a similar problem to one that has already had a thread, but may be a bit different. The problem: The PC has 2 HDD's (hd1) has Dapper which boots and performs fine.(hd2)Slave drive on which I installed Edgy 6.10. Edgy (hd2) will not boot (error 17). I have looked at boot menu list and it is on there. I have looked at fstab and the hd2 is there. I have looked at device map and both drives are there, however the output for device map is when I have disconnected drive 2. If I connect drive 2 and seek device map i get no output at all. When I first time boot with both drives connected to same IDE cable as master/slave, the boot sequence pauses a long time at the 'mounting root files' (second line in booting) but eventually boots. Now if I disconnect slave drive the boot sequence is normal and quick. Any help on this subject is greatly appreciated.

---

### Post by Sbarton on 2007-02-06
Re my first post I thought I may include attachments of device map and fstab + menu list if this helps.

---

