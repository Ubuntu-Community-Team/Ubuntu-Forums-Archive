---
title: "S-Video to TV Help!"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by Rileymd on 2007-11-30
Okay so I want to know if it's possible to set up my TV as a clone via an svideo cable in Linux...It works fine whenever I boot into Windows but not Linux, could someone guide me through how to get it working? I'm using Ubuntu 7.10 with an nVidia Geforce 7600gt Video Card connected to a tv via an svideo cable. Thanks!

---

### Post by Rileymd on 2007-11-30
I also posted this in the multimedia and video section yesterday but I believe this question is more suited for this section and no one answered it there so please don't flame me!

---

### Post by Emerzen on 2007-11-30
The answer is yes if you have an NVIDIA card as I know first hand.  Probably w/ ATI.  And I have no idea with integrated graphics.  If you have NVIDIA let me know and I can post the run through.

---

### Post by Rileymd on 2007-11-30
Yes I have an Nvidia card, a 7600gt if it really matters...Please help me!

---

### Post by forestpixie on 2007-11-30
have you got the restricted driver enabled - if yes ok - if not do that first.

Then run nvidia-settings
```
gksudo nvidia-settings
```

once in there - if the tv is connected and recognised but disabled. Click the image of the tv and then configure - I don't know what twinview (but I assume it shows the same as the monitor) or xinerama do because I have my tv as a separate x screen.

Make your changes, save to x config file and quit, restart and hopefully it'll work.

---

