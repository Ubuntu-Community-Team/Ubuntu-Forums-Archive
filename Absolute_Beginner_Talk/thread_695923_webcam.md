---
title: "webcam"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by sirfonners on 2008-02-13
I was never able to get my integrated webcam to work with anything except ekiga so I went out and bought the ***Logitech QuickCam Communicate STX*** because everyone said it should work with linux out of the box. 

so hear I am out of the box, plugged the camera in....aaand it doesnt seem to be doing anything.. what do I do?

---

### Post by sirfonners on 2008-02-13
do I have to like delete drivers for my integrated cam?

---

### Post by spiderbatdad on 2008-02-13
could you be more specific. what are you trying to do with the cam? Are you trying to video im through kopete, gyche, ekiga,....what? Are you trying to capture images or videos?  Have you installed any webcam software, like camorama?

---

### Post by sirfonners on 2008-02-13
I am trying to use stickam, on Ekiga I just got it so it uses the logitech cam
but when I go to option on stickam it doesnt even detect it

---

### Post by spiderbatdad on 2008-02-13
seems like possibly a problem with browser capability. maybe ubuntu-restricted-extras...adobe flashplayer...firefox might help. Are you using firefox?

---

### Post by sirfonners on 2008-02-13
> **spiderbatdad said:**
> seems like possibly a problem with browser capability. maybe ubuntu-restricted-extras...adobe flashplayer...firefox might help. Are you using firefox?

yeah I am using firefox, can you webcam with more than one person using ekiga or something?

---

### Post by spiderbatdad on 2008-02-13
sorry I haven't tried with more than one person. I use a logitech cam on gyache...a yahoo client, but only with my girlfriend. I did  try stickam for you last week. I was able to broadcast my cam,  but I didn't try a chatroom, with  multiple people viewing. I assume gyache would allow multiple viewing in a room...it works great in every application I've used it for.

---

### Post by sirfonners on 2008-02-13
its detects my integrated acer crystal eye cam, but it just shows a blank screen

but it wont give me the option to switch to my new logitech camera:confused:

---

### Post by spiderbatdad on 2008-02-13
you may have to blacklist the module of the onboard cam in /etc/modprobe.d/blacklist. and probably modprobe your usb cam.

Also CU-seeme looks interesting, but I've never tried it. [http://myhome.hanafos.com/~soonjp/vidconf.html](http://myhome.hanafos.com/~soonjp/vidconf.html)

I can try to help you with blacklisting and modprobe, but there are others who might offer better assistance. At any rate. I have to leave for a while. You might post the output from the following commands to assist us in assisting you.
```
lsmod
```

---

