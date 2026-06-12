---
title: "Installation problems on Old World. Powerbook and Wireless."
date: 2008-07-15
forum: Apple Hardware Users
---

### Post by Hover on 2008-07-15
I 've been spending a couple weeks trying to get Ubuntu installed on a 233MHz Wallstreet II Powerbook G3. First of all, Breezy works exceptionally well. but that doesn't quite help if I want to upgrade any software on it. 

However, on any newer release, I am unable to get an Aironet 350 to work. With the card present on boot, either after install or during, modprobe exits abnormally with the dump referencing problems with pcmcia_cs and cs. even after everything is all up and running, modprobe will crash when I try to load airo_cs (airo loads fine). blacklisting padlock_aes and geode_aes as kernel arguments doesn't seem to work.

I also have an Aironet A/B/G card. but I have been unable to get that to connect under Breezy even though Breezy sees it. And even then, it isn't recognized during installation. 

recap: Breezy works fine. Aironet 350 works. Aironet A/B/G recognized but unable to connect.

Anything newer than Breezy: Aironet 350 crashes the system. Aironet A/B/G not recognized.

I've also tried upgrading and leaving the 2.6.12 kernel, but that just brings pbbuttonsd to it's knees(dapper), or causes HAL errors(Hardy).


I do hope that somebody might still have experience with this interesting mix of hardware.

Thanks,
Hover

---

