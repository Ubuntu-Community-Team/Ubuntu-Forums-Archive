---
title: "[SOLVED] fatal server error: no screens found ATI 9250"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Ripfox on 2007-11-06
I have Kubuntu installed, but when I put in th ati 9250 and reboot it says no screens found. I tried the ati driver when i reconfigure xorg, same error.

---

### Post by P4man on 2007-11-08
Try this:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Ripfox on 2007-11-09
Yep, know that one. No go, thanks for the reply though, seems like I am getting less these days...:lolflag:

---

### Post by overdrank on 2007-11-09
> **ripfox said:**
> Yep, know that one. No go, thanks for the reply though, seems like I am getting less these days...:lolflag:

HI and it sounds like it is conflicting with the onboard graphics. Or does it have on board graphics?

---

### Post by Ripfox on 2007-11-09
Hi, thanks for the attention to my plight. I now have the ATI 9200 pro working with gutsy, and the desktop effects seem to be working. But no matter what option I select under screens for mu ILO tv as a second monitor with svideo, it flashes on then off. Any way to get svideo running?

---

### Post by Ripfox on 2007-11-09
bump

---

### Post by Ripfox on 2007-11-13
[http://ubuntuforums.org/showthread.php?t=215763](http://ubuntuforums.org/showthread.php?t=215763)

This worked for me. :)

---

