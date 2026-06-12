---
title: "[SOLVED] Cannot turn Compiz back on"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by firestormx37 on 2008-01-27
Hi I am running Gusty and had Compiz working great for the past few months.  I have a nvidia card, so I was originally using the restricted nvidia driver.  I then stopped using the restricted drivers and began using the drivers released by nvidia.  After installing those drivers, compiz still worked great.  Anyway, on to my problem.  When attempting to fix a problem that I have been having with suspend not working, I temporarily turned off Compiz by selecting None in the Appearance > Visual Effects tab.  This did not solve my problem so I went to turn Compiz back on, but now I am getting a message that the restricted driver is required to turn on Compiz.  I just had Compiz working without it.  Is there any way that I can force Compiz back on, or disable the check for the restricted driver.  I should also mention that I am still new to Linux, so specific instructions would be helpful.  Thanks.

EDIT:  I realize that I could go through the trouble of uninstalling my current drivers, reinstalling the restricted drivers, enabling compiz, uninstalling the restricted drivers, and reinstalling the current drivers, but I am looking for a simpler solution if anyone has one.

---

### Post by blueridgedog on 2008-01-27
I recommend you try and install the compiz fusion icon:

sudo aptitude install fusion-icon

It is a small tool that will let you pick your window manager and window decorator.  Mine resides in the try, it is for some odd reason invisible, but works non-the-less.

Once running, right click the icon, select window manager, select compiz, then select emerald as your window decorator.

It might work.

---

### Post by firestormx37 on 2008-01-27
Thanks for the advice.  I got it working using a similar workaround.  I had GL Desktop installed too and was able to enable it through that.  Now I can change my compiz settings as usual.

---

