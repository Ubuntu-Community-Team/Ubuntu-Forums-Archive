---
title: "Network connection issues"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by drunkardivan on 2007-11-11
Hello all.

I think I've screwed up. My wife wanted Ubuntu, and Ubuntu alone, on her notebook PC (she's going through a serious anti-MS stage right now). So, I installed it for her, got everything running well... except the internet connection. I'm running a LinkSys WRT54GS router with WPA TKIP... and her Gutsy just would not recognize the WPA connection. So, I thumbed around, and someone turned me on to Wicd. A little Googling, and it looked like the answer to my problems. 

If it was, I wouldn't be writing this.

Now, not only does it not see my home network, it won't even connect to my neighbor's unsecured signal.

If anyone has any ideas, please let me know.

Oh, and her computer's an emachines w340, the wireless card is a RealTek 8180.

---

### Post by HermanAB on 2007-11-11
You'll have trouble with WPA.  In my experience it is still too buggy to bother with.  I suggest that you change your router to WEP.  That is good enough for home use.

Cheers,

Herman

---

### Post by drunkardivan on 2007-11-11
WEP isn't an option- I like having a secure network, and WEP doesn't provide that.

I'm narrowing down the problem, slowly but surely...

It looked like Wicd was the solution, so I opened that up... and now, I can't even connect on my neighbor's unencrypted signal. Ran iwconfig, and saw that Wicd is trying to connect to my router, but it's looking at the wrong MAC address: xx.xx.xx.xx.0F, instead of 0D.

---

### Post by alterKrieg on 2007-12-18
Did you figure out a fix for this?  I'm having the same issue.  I can connect to unsecured networks now, but no WPA.

---

### Post by daimaru on 2007-12-18
> **HermanAB said:**
> You'll have trouble with WPA.  In my experience it is still too buggy to bother with.  I suggest that you change your router to WEP.  That is good enough for home use.

Cheers,

Herman

please dont change to WEP anyone with a bit of knowledge can crack that in under 1.5 minutes....

---

### Post by x-to-tha-t on 2007-12-18
Hey all... I just might have what you all are looking for... Use WiCD... Website is [wicd.sourceforge.net/](wicd.sourceforge.net/)... I had all sorts of issues with getting Ubuntu to reconginse my Linksys WAG200G with WPA but WiCD allows not only WPA but also supports static IP (useful if you use torrents). I am totally impressed with it.

---

