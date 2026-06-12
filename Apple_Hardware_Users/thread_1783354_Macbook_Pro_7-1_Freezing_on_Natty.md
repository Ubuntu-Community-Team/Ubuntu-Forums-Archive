---
title: "Macbook Pro 7-1 Freezing on Natty"
date: 2011-06-15
forum: Apple Hardware Users
---

### Post by mbarvian on 2011-06-15
Hey guys,

As of recently, both Natty and Maverick have been freezing on my Macbook Pro 7,1 (mid 2010), to the point that I have to force shutdown (which I can't stand doing).  It happens every <10 minutes, sometimes less than 2 minutes from booting.  It's frustrating beyond belief, usually because I'm in the middle of something when it happens.

I think it might be related to my wireless card, as I've had problems with it before on this machine.  I'd attach kernel logs, but I don't want to boot into Ubuntu again on that machine.

I can usually predict when it will happen, because I'm using browsing the web on Chromium and all of a sudden it will get stuck on "Sending request...." when trying to load something.  After that point, I'm screwed. If I try turning off the wireless, it freezes.  If I try restarting, it'll hang on shutdown.

Any help would be greatly appreciated!!

Thanks,
Max

---

### Post by parananon on 2011-06-15
I had a random freezing problem when using Natty on my Macbook Air (Late 2010). It didn't seem to happen once I switched to Ubuntu Classic from the login screen however. Once I followed all the instructions on [this]("https://help.ubuntu.com/community/MacBookAir3-2/Meerkat") page, Ubuntu hasn't frozen since, even in the new Unity desktop. (As a side note, I had to remove ```
Section "InputClass"
    MatchIsTouchpad "true"
    Identifier "Multitouch Touchpad"
    Driver "multitouch"
EndSection
```
Even though the file told me to add it. Good luck!

---

### Post by mbarvian on 2011-06-16
> **parananon said:**
> I had a random freezing problem when using Natty on my Macbook Air (Late 2010). It didn't seem to happen once I switched to Ubuntu Classic from the login screen however. Once I followed all the instructions on [this]("https://help.ubuntu.com/community/MacBookAir3-2/Meerkat") page, Ubuntu hasn't frozen since, even in the new Unity desktop. (As a side note, I had to remove ```
Section "InputClass"
    MatchIsTouchpad "true"
    Identifier "Multitouch Touchpad"
    Driver "multitouch"
EndSection
```
Even though the file told me to add it. Good luck!

I can't verify for sure just yet, but it definitely seems to be working! No freezes yet! :D

Thanks a lot!

---

