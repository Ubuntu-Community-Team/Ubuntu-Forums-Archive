---
title: "Stickam?"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by sirfonners on 2008-02-07
So I finally just got my webcam working for Ekiga, So I went to stickam so I could webcam with some friends like I was trying to all along. But when I click the allow button so that stickam can access my webcam nothing happens, it just stays a black screen.

Now I read something about using the VLC player and such but it didnt work

anyone have any ideas on what to do?

---

### Post by papuccino1 on 2008-02-07
Do you have the correct drivers, and can you use the camera offline like an a recording aplication?

---

### Post by spiderbatdad on 2008-02-07
sounds like those other programs have some unmet dependencies...the way gyache depends on imagemagic for its webcam features...gyache works  great by the way.

---

### Post by spiderbatdad on 2008-02-07
hmmm just tried stickam...worked fine. Maybe try installing imagmagic from synaptic

---

### Post by loell on 2008-02-08
uhmm, actually, gyache uses imagemagick tools, only for avatar conversion and resizing,  
it however uses **libjasper** for viewing and uploading webcam stream images. both imagemagick and libjasper is installed automatically when you install the software via binary package.

maybe stickam had different models which works and doesn't work with linux, 

both of you can do **lsusb** and post your output here, so we could compare.

---

### Post by spiderbatdad on 2008-02-08
Bus 002 Device 002: ID 046d:0870 Logitech, Inc. QuickCam Express

---

### Post by 449 on 2008-02-17
I have the same problem.

Bus 005 Device 006: ID 041e:4063 Creative Technology, Ltd

---

### Post by ericstoesser on 2008-03-09
me too 
 05a9:2640 OmniVision Technologies, Inc.

---

