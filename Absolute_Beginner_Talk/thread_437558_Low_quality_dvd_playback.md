---
title: "Low quality dvd playback"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by jonward0690 on 2007-05-08
When I put a dvd in to watch, the movie studders and I have all the plugins instaled

---

### Post by [ajax] on 2007-05-08
What video card are you using?  Do you have the proper drivers installed?  It sounds as if you don't have direct rendering.  Type "glxinfo" into the terminal to find out.

---

### Post by nanotube on 2007-05-08
maybe you need to enable dma? whats your output of 
```
hdparm /dev/dvd
```

---

### Post by jonward0690 on 2007-05-09
> **nanotube said:**
> maybe you need to enable dma? whats your output of 
```
hdparm /dev/dvd
```


/dev/dvd:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
jon@jon-desktop:~$ 

This is what i get in the terminal.

---

### Post by nanotube on 2007-05-09
so, doesn't look like there's dma... try the following instructions:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Choppy_DVD_playback.3F](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Choppy_DVD_playback.3F)
(but instead of /dev/hda, use your /dev/dvd (just in case your dvd drive is not on /dev/hda)

---

### Post by jonward0690 on 2007-05-09
> **nanotube said:**
> so, doesn't look like there's dma... try the following instructions:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Choppy_DVD_playback.3F](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Choppy_DVD_playback.3F)
(but instead of /dev/hda, use your /dev/dvd (just in case your dvd drive is not on /dev/hda)

Thanks for the info it fixed my problem.

---

### Post by nanotube on 2007-05-09
excellent! :)

---

