---
title: "Nas Drive Help"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-08-18
I am a NAS drive newb, and have a few questions. Basically what I want to do is to create an back-up storage website where I can back-up all of my files and be able to download and upload the files from practically anywhere. I know that I can do this with a webhost, but for a variety of reasons, I want to have my own server.

With sites such as [www.dyndns.com](www.dyndns.com), I can get a free domain name, but I have to provide my own server like a NAS or FTP server.

I would greatly appreciate if you could help me decide how to pick out a NAS server.

The primary concerns that I have are speed, reliability, and storage space.

I want my Nas drive to have a good upload speed and good download spped. 

I need it to be reliable. I do not want it to be down unless the power is turned off and potentially have RAID.

I would like to put several hundred GB up to a potential few TB of storage space in it.

I would appreciate if you could recommend any good NAS drives and give me links to learn more about NAS drives. I do not want to have to mess around with configuring it, I want it to be able to work out right out of the box. 

Any and all help is appreciated.

Thanks


:guitar:

---

### Post by cbhargava on 2007-08-19
You can easily roll out your own NAS but I doubt that you will get any web storage capability.

Build your machine with sata drives and a sata raid controller. For software use [FreeNAS]("http://www.freenas.org/index.php?option=com_frontpage&Itemid=1")

You should also be able to tailor that software to your needs.

---

