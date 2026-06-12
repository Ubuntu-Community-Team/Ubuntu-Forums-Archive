---
title: "ATI Radeon RV350 - psychodelic colors"
date: 2017-01-10
forum: Apple Hardware Users
---

### Post by cyberbobak on 2017-01-10
Hello all,

can somebody please advice how to configure the card in Ubuntu MATE 14.04 ? 
```

lspci | grp -i vga

0000:f0:10.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV350 [Radeon 9550/9600/X1050 Series]

Not working:
video=radeonfb:1920x1080-32 

radeon.modeset=1 video=offb:off video=radeonfb:off video=1920x1080-32 radeon.agpmode=-1

video=radeonfb: off video=offb:off radeon.agpmode=-1

video=ofonly  radeon.agpmode=-1 

radeon.modeset=0 video=radeonfb:1280x960-32@60 - NO 
```

I also played with xorg.conf without luck.

Thank You

---

### Post by luigiburdo on 2017-01-15
hi did you have a powerpc machine ? if yes probably is because of this. BE is really bad supported on mesa and xorg

---

### Post by cyberbobak on 2017-02-03
Hi, sorry for late response, yes I've PowerMac G5

---

