---
title: "2 problems: SLOW CD ripping (2x) and VLC has no sound with avi's"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by sdubois92 on 2006-11-09
2 problems: SLOW CD ripping (2x) and VLC has no sound with avi's

Every CD rippingprogram I tried does it at the same speed.

In VLC, when I play an AVI, it plays fine, except theres no sound. My sound card is a cs4235 and im using alsa. any help?

---

### Post by Bachstelze on 2006-11-09
1) DMA enabled on your CD-ROM drive ?

2) *sudo apt-get install vlc-plugin-alsa*

---

### Post by den benne on 2006-11-09
is dma on?
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_speed_up_CD.2FDVD-ROM](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_speed_up_CD.2FDVD-ROM)

---

### Post by Volfied on 2006-12-24
Allright I was having the same problem, try this:
Audio > Audio Devices > Stereo

some other thing was chosen and all avi files kept on giving this ticking sound with picture clear, but with stereo it works fine

Hope this helps

---

