---
title: "Configuring video card in command line..please help?"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by madu on 2006-02-01
Hi guys..

I changed my video card pci-x bandwidth from x2 to x8  and then when I logged to Ubuntu it gave me an error saying the card was changed.. and I could not get in. I only got the command line.
Can anybody tell me the command I have to give to enter the configuration.. ?
Thanks a lot guys!

---

### Post by DiscoKiller on 2006-02-01
u could try

 sudo dpkg-reconfigure xserver-xorg

this may help you get your video back. accept all defaults if u are unsure


DK

---

