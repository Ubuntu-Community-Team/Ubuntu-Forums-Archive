---
title: "need help! reconfiguring xorg"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-10-06
I am trying to reconfigure the x server using

```
 sudo dpkg-reconfigure xserver-xorg 
```

and it is now asking: Please enter video card's bus identifier

What does this mean?

I have a Radeon X1600pro AGP 8x gpu

---

### Post by bulldog on 2006-10-06
I have no experience with ATI but when I look in my xorg.conf there is```
 BusID         "PCI:1:0:0"
```

And maybe it's more easy to use ```
sudo dpkg-reconfigure -phigh  xserver-xorg
``` this should 'autodetect' most settings for you.

---

### Post by WalmartSniperLX on 2006-10-06
> **bulldog said:**
> I have no experience with ATI but when I look in my xorg.conf there is```
 BusID         "PCI:1:0:0"
```

And maybe it's more easy to use ```
sudo dpkg-reconfigure -phigh  xserver-xorg
``` this should 'autodetect' most settings for you.

Thank you VERY much! :D

---

### Post by Portable_Jim on 2006-12-01
Thanks also - same problem, same solution.

---

