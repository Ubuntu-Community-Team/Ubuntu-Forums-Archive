---
title: "Ubuntu 10.10 Macbook 4,1"
date: 2010-11-08
forum: Apple Hardware Users
---

### Post by rakevinwr on 2010-11-08
I have just finished triple booting my macbook 4,1 with WIndows 7, Snow Leopard and Ubuntu 10.10

At first everything was working 100% and then I spent a good 2 hours getting the isight webcam to work.

Now the webcam works perfectly but somehow I messed up my sound? No input or output.

I followed a guide after some reading on the internet and added 

```
options snd-hda-intel model=imac24
```

to /etc/modprobe.d/alsa-base.conf

and I am getting output through my speakers again but still no input from the microphone!?

Anyway anyone can help me figure this out? <3

---

### Post by linuxopjemac on 2010-11-09
Did you unmute all channels with 
```
alsamixer
```
?

---

### Post by theSuperman on 2010-11-09
Usually the mic is muted after adding that line to the alsa-base.conf and rebooting.

---

