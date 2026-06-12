---
title: "NVidia  TNT2 Riva AGP card"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by SnowLinux on 2007-05-14
Installing Edubuntu 7.04 but only get basic resoltion and refresh of 60Hz

I need a practical way to get 1152 x 864 @ 75hx - what do I do?

---

### Post by wirelessmonkey on 2007-05-14
What video card are you using?  You need to make sure you've installed the correct drivers for that card.

---

### Post by Kobalt on 2007-05-14
See this : [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-7f830fe17ae6da7c546decbb10c32ff61471258e](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-7f830fe17ae6da7c546decbb10c32ff61471258e)

---

### Post by SnowLinux on 2007-05-17
The card is NVidia TNT2 Riva AGP card as marked on the box it came in
and is fitted into a x8 AGP lsot on an Asrock motherboard.

Just out of interest which driver sholud I have installed for the card.
When I search for TNT2 in the software manager there are three options available.

---

### Post by Neil Purling on 2007-05-17
How many Mb memory on the video card.?
I have a 16Mb NVIDIA RIVA TNT2 PCI slot destined for a backup Linux box so I am watching this thread with interest.

---

### Post by SnowLinux on 2007-05-17
My Nvidia  TNT2 Riva AGP card has 32MB Of memory.

I've installed Edubuntu 7.04 on an older AMD system as well
with on board SIG graphics, sound, LAN and all were picked up well,
the graphics in fact went to 1164x860 by default, just had to increase
refresh from 60 to 75Hz.

Once I get my Nvidia  TNT2 Riva AGP graphics sorted I'll very content!

---

### Post by SnowLinux on 2007-05-17
All sorted
I looked around the forum and found snippets about editing xorg.conf
and did just that after installing nvidia glx legacy drivers.

Adjusted Horizontal sync upto 95 and Vertical refresh upto 160
and added refresh of 1152x864, saved and rebooted.

Now I've got what I want.

By the way, can any one tell me how Horizontal sync and Vertical refresh 
effect refresh rate please?

---

