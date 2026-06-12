---
title: "refresh rate"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Sterbik on 2006-11-09
When i installed ubuntu i noticed that the resolution and refresh rate is not okay. But thank's to you i successfully repaired the resolution, i even got more options for refresh rate's. I choosed 85 Hz for my 17 inch Samsung 793 DF monitor which is working like it should be only 70Hz in windows. Actually i'm using only 75HZ in windows and it's MUCH better than ubuntu's 85HZ.I think that the driver for my ati radeon 9600 se is not working perfectly. Is there some kind of fix for this?

---

### Post by taurus on 2006-11-09
Maybe you want to reconfigure your X again with (Applications -> Accessories -> Terminal)

```

sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak <-- make a backup copy in case you need to get it back...
sudo dpkg-reconfigure xserver-xorg

```
Or you can also edit /etc/X11/xorg.conf and make changes directly from there...

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Sterbik on 2006-11-11
I wrote the last code into the terminal which you told me. This is a too complicated for me, i'm just a newbe, is there an easier way?

---

