---
title: "Entering quotation marks"
date: 2008-05-17
forum: Apple Hardware Users
---

### Post by jamescoy on 2008-05-17
Every time I try enter quotation marks when editing a config file in the Terminal, I have to push the quotation key down twice, and even then the character doesn't appear correctly. The quotation marks looks almost like "smart" quotation marks; consequently, my entries sometimes ending up being invalid because of this anomaly.

I'm sure there's a simple fix here for this....I'd appreciate some guidance.

---

### Post by Patb on 2008-05-17
James, this sounds like an incorrect default keyboard layout.  I'm not sure there is a simple fix which will completely cure this problem.  I had the same problem with an earlier release of Ubuntu and ended up reinstalling and choosing my correct keyboard layout manually during install.  

But before being so radical, try backing up your xorg.conf and then reconfiguring:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak1
sudo dpkg-reconfigure xserver-xorg
```
It will ask you a few questions. Try a different keyboard layout.  You will probably need to log out and log back in to test it.  

Cheers, Pat.

---

