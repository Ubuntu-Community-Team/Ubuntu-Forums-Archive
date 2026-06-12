---
title: "Upgrade to Feisty: DMA fails on DVD playback"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Mega_Fauna on 2007-04-29
Hi,

After I upgraded to Feisty the DVD playback became really choppy so I tried to enable DMA but it fails. I have googled this and don't understand the various discussions. How do i fix this pls?

**I enter: **
```
sudo hdparm -d1 /media/cdrom1
```

**It outputs: **
```
/media/cdrom1:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
```

---

### Post by chalewa on 2007-05-01
everyone is having this same problem...

---

### Post by Mega_Fauna on 2007-05-01
I figured out last night that my DVD's played smoothly when I turnt off Beryl and went with Ubuntu's default Gnome Metacity window manager.

I had that ioctl error a second time though when extracting a .rar file. to my hd which worried me (I couldn't open the file); so my DMA is still off and there are other quirks as well, but at least I can watch DVD's.

---

