---
title: "Did I screw up my install?"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by ErsatzM on 2006-07-25
I was scouring the internet for Ubuntu optimization tips about screen resolution and getting more --Hz display choices. I came across one page that suggested to install the appropriate driver for my graphics chip. I thought I had an ATI chip when I didnt, so I installed their driver and now Ubuntu will only load into text mode. I tried typing in startx and a bunch of junk came up, with this at the end: [IMG]http://img157.imageshack.us/img157/3226/post207221101669243wr5.jpg[/IMG]

](*,)

---

### Post by VirtuAlex on 2006-07-26
Do ls /etc/X11 and see if by some chance you have a bakup of xorg.conf
If not do dpkg reconfigure xserver-xorg and choose right driver

---

### Post by JerMe on 2006-07-26
Try reverting back to the old config:

```
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install --reinstall libgl1-mesa
```

I *think* you installed the fglrx driver for ati cards, so to remove it, you'd do this:

```
sudo apt-get remove xorg-driver-fglrx
```

plus undo whatever else you did.  Good luck

---

