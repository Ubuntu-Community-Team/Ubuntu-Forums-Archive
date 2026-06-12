---
title: "Cups: Quota exceeded"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Error403 on 2007-09-08
Hi, I recently got the Cups error User quota exceeded and wasn't able to print anymore.

Following a few posts here and there, I finally agreed to myself to reinstall the printer driver. Now it works fine, but for how long?  I really need some help to keep printer sharing working without any more hiccups like that, so where can I either disable quotas, or beef up my user's quota limits?

I have a Samsung ML-2510 laser printer on Ubuntu 7.04

I have included my smb.conf cupsd.conf and printers.conf (as txt or won't upload!)  for peeking.

Thanks!

---

### Post by p_quarles on 2007-09-08
You probably unintentionally set a quota at some point during the previous installation. Your "printers.conf" file has quotas turned off, so you shouldn't have this problem again unless you mess with it.

By the way, you can administer stuff like quotas from CUPS web interface. Point your browser to:
```
http://localhost:631
```

---

### Post by Error403 on 2007-09-08
Thanks p_quarles for your answer.  
I tried to disable/find anything that has anything to do with quotas, but never found it, even through localhost:631.  Oh well, I'll keep my fingers crossed.

---

