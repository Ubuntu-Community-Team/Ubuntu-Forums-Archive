---
title: "Newb With No CD Sound"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by radioraheem on 2006-03-24
I can rip mp3's from CD but I can't get any actual sound when trying to just play a CD.

Need some guidance here... thanks all.

---

### Post by akiro.yamamoto on 2006-03-24
Unless the CD-ROM drive has an audio cable connected to your sound card (analog) you will have this problem. I think you can still use XMMS to play your CDs. Just ensure you have DMA enabled for your drive (to prevent choppy sound).
Startx XMMS ,  Right <Click> , select Preferences (see pic)
Click on the CD Audio Plugin <click> Configure and Configure similar to my pic.
At this point just add the CDs contents to your Playlist and you should be good
to go ;)

---

### Post by akiro.yamamoto on 2006-03-24
Check for dma on that drive....
```

hdparm -d /dev/hdc (/dev/hdc is my CD drive YMMV )
sudo hdparm -d1 /dev/hdc (set DMA to ON for /dev/hdc)

```

Hope this info helps ;)

---

### Post by imike on 2006-03-24
Don't forget not to mute your CD-ROM audio settings :)

---

