---
title: "edgy / tv-out - please help"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by Esben Kramer on 2006-10-31
Can somebody please help me? I can't get the TV-out working in Edgy. I tried following a guide (momentarily stranding me with a broken X, but it was easily fixed). Could somebody please guide me to good guide for Edgy?

---

### Post by theicyj on 2006-10-31
Are you using an ATI card?  I was able to get DVI and S-Video both working right out of the box in Edgy with an ATI Radeon 9000 and a 9250 card.  The catch with getting s-video working for me was to _NOT_ use a s-video-to-RCA adapter, but a plain s-video cable.  Hope this helps.

---

### Post by Esben Kramer on 2006-10-31
I use Nvidia and a direct s-video cable. I got it working in Dapper, by playing with the xorg.conf, but it won't work in edgy. Can I see your xorg.conf?

---

### Post by Esben Kramer on 2006-10-31
Or anybody elses, for that matter? Could somebody who has a working TV-out in edgy please post their xorg.conf-file for me?

---

### Post by marx2k on 2006-10-31
> **theicyj said:**
> Are you using an ATI card?  I was able to get DVI and S-Video both working right out of the box in Edgy with an ATI Radeon 9000 and a 9250 card.  The catch with getting s-video working for me was to _NOT_ use a s-video-to-RCA adapter, but a plain s-video cable.  Hope this helps.

Ive actually been trying to get the TV out on my ATI Radeon 9000 to work in edgy for 6 days now with no luck.  Can you detail the steps you took to get this to work?  Or was it working 'out of the box' and the only thing you did is a straight-through s-video?

I currently have my svideo out connected to a box that works as a 'connector' that also has an s-video out that connects into the TV.

Works in Windows (if connectivity is the problem) but not in Edgy.

So PLEASE do a guy a favor and let me know!

---

### Post by theicyj on 2006-10-31
Besides using a straight through s-video cable (as I already noted, the s-video-to-RCA adapter didn't work for me) I installed the ATI driver as per instructions here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")  To be honest, I am not sure if the the video-out was working before or after I installed the driver.  I didn't change the xorg file manually at all.  One other note, I had the s-video cable connected before starting the computer and no computer monitors were attached.  Otherwise it was a fresh copy of Edgy.

---

### Post by Esben Kramer on 2006-10-31
I've been looking around, and this seems to be a very normal problem. Not unsolvable, though.

EDIT: I got it working witt nvidia. Quite a hassle though. My problem was with the beta-drivers on Edgy. They don't autodetect the TV, like they should. It seems that it's as simple as using nvidia-settings. Doh! Hope this helps some of the nvidia-people with headaches out there.

---

### Post by marx2k on 2006-11-01
> **theicyj said:**
> Besides using a straight through s-video cable (as I already noted, the s-video-to-RCA adapter didn't work for me) I installed the ATI driver as per instructions here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")  To be honest, I am not sure if the the video-out was working before or after I installed the driver.  I didn't change the xorg file manually at all.  One other note, I had the s-video cable connected before starting the computer and no computer monitors were attached.  Otherwise it was a fresh copy of Edgy.

What version of the drivers did you install? 8.28.8? I think edgy auto-installed that for me and it didn't work correctly.  From what I readm 8.25.* is the one that works?

---

### Post by theicyj on 2006-11-01
I think I installed 8.28.8.  I can maybe double-check this weekend.

---

### Post by jetpeach on 2006-11-04
i can't get the tv-out working on edgy either, using nvidia geforce3 ti200.  if anybody who has it working can post xorg.conf much appreciated!

EDIT: I believe the problem was with the nvidia drivers that came with edgy, they failed to use the tv-out only.  I upgraded to the beta drivers (there is a howto on these forums somewhere) and that fixed the problem

---

