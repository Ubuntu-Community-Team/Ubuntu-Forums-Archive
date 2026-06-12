---
title: "OT (slightly) itunes over samba"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by cnschulz on 2007-06-16
Hi,

Ive just moved my server from XP to Ubuntu and all works brilliantly except itunes over samba.

I have my itunes library (xml) and mp3s located on a samba share and run itunes from an XP client.

I can stream movies, copy at full speed and have blindingly fast internet but I cant play an mp3 through itunes.

Ive monitored the network traffic on XP and itunes just kills the network!

I have tuned samba+XP setting MTU, SND+RCV and oslevel settings to optimal. It is ONLY ITUNES that cripples the network!

Please have a look at this image from my network monitor:

[http://cnschulz.homeip.net/itunes.wtf.JPG]("http://cnschulz.homeip.net/itunes.wtf.JPG")

Any help appreciated.

---

### Post by cnschulz on 2007-06-28
performance is *much* better when i run samba over an ext3 disk rather than ntfs... obviously ntfs-3g has some overheads.

c.

---

### Post by jd65pl on 2008-01-11
Try sharing files to itunes using mt-daap [here]("http://jamiedumbill.com/index.php?page=28") is a how to

---

