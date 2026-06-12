---
title: "new macbook - bcm4328 wifi?"
date: 2007-11-14
forum: Apple Intel Users
---

### Post by houseofmore on 2007-11-14
Anyone have any luck with Gutsy and the bcm4328 wifi driver that ships with the new macbooks?

---

### Post by cleentrax on 2007-11-14
> **houseofmore said:**
> Anyone have any luck with Gutsy and the bcm4328 wifi driver that ships with the new macbooks?

No luck for me yet, in 64-bit Gutsy. I've had success getting the driver installed with ndiswrapper, but the wifi doesn't show up as a usable networking option.

[http://ubuntuforums.org/showthread.php?t=607300](http://ubuntuforums.org/showthread.php?t=607300)

---

### Post by houseofmore on 2007-11-14
Bugger.  Looks like its back to OSX for a while :|

---

### Post by Seq on 2007-11-15
I think a few people have had trouble with ndiswrapper on the new macbook, but it worked fine for me the first time. There does appear to be a random freeze that happens (pretty rare, maybe once a day), but enough to be annoying. It did not happen at all before I started using ndiswrapper, so I have attributed it to that.

---

### Post by cleentrax on 2007-11-15
I replaced Ubuntu Studio with 7.10 64-bit, and now the ndiswrapper works with the Broadcom 4328. It's a bit flaky, but it works.

---

### Post by cyberdork33 on 2007-11-15
> **cleentrax said:**
> I replaced Ubuntu Studio with 7.10 64-bit, and now the ndiswrapper works with the Broadcom 4328. It's a bit flaky, but it works.

Ah Ha! I knew it was something like that... You may have been able to stick with Ubuntu Studio, just use the standard kernel rather than the rt kernel. Too late now I guess.

ndiswrapper has it's quirks as well, but it is usually not as bad as bcm43xx for me. At least you got it working.

---

### Post by Seq on 2007-11-15
I just ordered a macbook atheros-based card on ebay. About $50, but probably worth it in the long run.

---

### Post by FunkyM on 2007-11-15
The iMac 24" has the exact same chip and I am using it with ndiswrapper without any issues. There is no opensource driver for this available yet.

---

### Post by cyberdork33 on 2007-11-15
> **FunkyM said:**
> The iMac 24" has the exact same chip and I am using it with ndiswrapper without any issues. There is no opensource driver for this available yet.
Yes, all the Intel iMacs have it.

---

### Post by cleentrax on 2007-11-15
> **cyberdork33 said:**
> Ah Ha! I knew it was something like that... You may have been able to stick with Ubuntu Studio, just use the standard kernel rather than the rt kernel. Too late now I guess.

ndiswrapper has it's quirks as well, but it is usually not as bad as bcm43xx for me. At least you got it working.

Thanks so much for all your help. Now I just have to fix suspend, the trackpad, the keyboard and the sound. :)

---

### Post by Seq on 2007-11-15
> **cleentrax said:**
> Thanks so much for all your help. Now I just have to fix suspend, the trackpad, the keyboard and the sound. :)

cleentrax, I built packages with the appletouch and keyboard patches in them (they are in the other thread we were in), have you tried them?

---

### Post by cleentrax on 2007-11-15
> **Seq said:**
> cleentrax, I built packages with the appletouch and keyboard patches in them (they are in the other thread we were in), have you tried them?

Wasn't sure how to proceed. Are those kernel patches?

---

### Post by cyberdork33 on 2007-11-15
> **cleentrax said:**
> Thanks so much for all your help. Now I just have to fix suspend, the trackpad, the keyboard and the sound. :)
Suspend is going to be the hard one likely. This is hard on all newer hardware. 

I thought there was a posted fix for the trackpad...
EDIT: See above posts

For the sound, you might try compiling the newest release of ALSA, like the Mac Pro users have to do:
[http://ubuntuforums.org/showthread.php?t=518391](http://ubuntuforums.org/showthread.php?t=518391)

---

