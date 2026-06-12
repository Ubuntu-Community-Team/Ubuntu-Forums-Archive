---
title: "Problems with macbook touchpad"
date: 2007-05-28
forum: Apple Intel Users
---

### Post by johnficca on 2007-05-28
Hi I just installed Ubuntu 7.04 on a friends macbook core 2 duo, the good news is it was easy and the new madwifi driver is working great. The problem I'm having is the trackpad or touchpad is acting up, it just stops for like a second or two like three times a minute...very annoying. It also seems to be very sensitive at times clicking for no reason, but I think I fixed the sensitivity with fingerhigh fingerlow options but not the stoping. I've tried everything you can think of in the xorg.conf file and its ALWAYS the same. Is this a bug, is there a fix ? 

Please let me know what you know thanks

---

### Post by ronocdh on 2007-05-29
Trying installing Qsynaptics or Gsynaptics. I recommend the former, but I think the latter is more popular. There's hardly a difference, I guess. You'll have to add ```
Option     "SHMConfig"    "true"
```to your xorg.conf under the section for your trackpad for these to work (only install one).

Also, you may want to add them to your startup so they'll load upon login.

---

### Post by zurgutt on 2007-05-29
Installing Qsynaptics or Gsynaptics wont solve this problem.  I know, have tried everything in the forums here, nothing helps.  Trackapad just is unresponsive and cursor stops now and then.

I think problem must be with new Core 2 Duo macbooks and the appletouch kernel driver, it is not correctly calibrated or something.  All other livecd distributions except feisty work fine.

I wonder how to disable appletouch and let same alternative driver take over that others use?  Just blacklisting appletouch module does not seems to work.

---

### Post by ronocdh on 2007-05-29
> **zurgutt said:**
> Installing Qsynaptics or Gsynaptics wont solve this problem.  I know, have tried everything in the forums here, nothing helps.  Trackapad just is unresponsive and cursor stops now and then.

I think problem must be with new Core 2 Duo macbooks and the appletouch kernel driver, it is not correctly calibrated or something.  All other livecd distributions except feisty work fine.

I wonder how to disable appletouch and let same alternative driver take over that others use?  Just blacklisting appletouch module does not seems to work.
No, just installing those things won't help, as my post indicated. There are two additional steps you'll have to take. With those done, you should see an increase in performance. I have never heard of someone configuring these drivers correctly (i.e. following my instructions above) and still suffering some poor performance. It is very change that you notice no improvement, when that's the same symptom of not having configured the driver after installation, which I see often and which I have done (several times!) myself.

Please post more information about your problem and your hardware if you wish to troubleshoot it further.

---

### Post by thully on 2007-05-29
I have an opposite experience - no matter what Qsynaptics/Gsynaptics settings I've used with my MacBook, I'm left with a somewhat unresponsive cursor - there is one tracking speed, and it is *sluggish*.  Changing the acceleration settings has no effect whatsoever.  

What I've done is to disable the appletouch driver - which seems to be not-ready-for-prime-time - and just use the generic usbhid driver.  It's not great to lose the advanced functions (tapping, scrolling, etc - though I personally hate tapping...), but the cursor speed is improved and is actually adjustable (unlike with appletouch).  If you do this, I suggest mapping keys to replace some of the advanced mouse features. 

I don't have my MacBook now, though, so I can't get the exact settings - I do know it would involve blacklisting some modules (appletouch notably) and editing the xorg.conf file.

---

### Post by diderot5 on 2007-07-22
Well, I have tried multiple versions of Ubuntu on both my MacBook and my iBook and I have always had this problem.

It's why I don't use Linux.

---

### Post by cyberdork33 on 2007-07-23
> **diderot5 said:**
> Well, I have tried multiple versions of Ubuntu on both my MacBook and my iBook and I have always had this problem.

It's why I don't use Linux.

I believe that most of these problems are fixed in the newer kernel / mactel patches.

---

