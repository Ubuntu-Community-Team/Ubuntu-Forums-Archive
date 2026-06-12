---
title: "Very bad sound quality with mac os x"
date: 2008-08-09
forum: Apple Hardware Users
---

### Post by ZachS on 2008-08-09
I have a imac Santa Rosa and I get very bad sound quality with it, where the sound is hollow. I enjoy music a lot but I'm tired of this bad quality in Ubuntu. What is my problem here?

---

### Post by cyberdork33 on 2008-08-10
If you are saying you have an aluminum iMac, try adding 

```
options snd-hda-intel model=imac24
``` to /etc/modprobe.d/alsa-base

---

### Post by ZachS on 2008-08-10
sorry but i am very new to linux, how would you add a command?

---

### Post by cyberdork33 on 2008-08-10
> **ZachS said:**
> sorry but i am very new to linux, how would you add a command?

Open the file in your text editor with root permissions (so that you can edit it)
```
gksudo gedit /etc/modprobe.d/alsa-base
```

then literally add 'options snd-hda-intel model=imac24' to the file and save. Then reboot.

---

### Post by ZachS on 2008-08-11
I have a 20 in. iMac, shouldn't it be imac=20?

---

### Post by cyberdork33 on 2008-08-11
> **ZachS said:**
> I have a 20 in. iMac, shouldn't it be imac=20?
I don't think that option exists, but it doesn't really matter anyway as it is the same hardware. You can try it... it wouldn't hurt anything. that would be "model=imac20" btw...

---

### Post by sayad on 2008-08-11
reinstal the driver and see - these problems are really irritating and tehy have been irritating me for long tim e- and now i fianally had to change from my apple pc , thus try and try re installing the driver.
Also you could check if you are using some competitible version of teh apple you are using.

---

