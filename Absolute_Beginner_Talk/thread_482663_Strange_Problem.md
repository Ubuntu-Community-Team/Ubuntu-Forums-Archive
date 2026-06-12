---
title: "Strange Problem"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by thelemech on 2007-06-23
Just installed on a P2 400 MHz 320 Mb Ram - everything works wonderfully excluding the internet- internet will not work unless live cd is in drive and following first reboot after live cd - following this neither Ubuntu or Windows XP cannot access internet?(dual boot-system)
Any ideas?

---

### Post by yabbadabbadont on 2007-06-23
Try doing a cold boot and see if it works.  i.e. poweroff, then start back up.

---

### Post by arcooke on 2007-06-23
> **thelemech said:**
> Just installed on a P2 400 MHz 320 Mb Ram - everything works wonderfully excluding the internet- internet will not work unless live cd is in drive and following first reboot after live cd - following this neither Ubuntu or Windows XP cannot access internet?(dual boot-system)
Any ideas?

This happened to me today actually (only the LiveCD would connect to the internet). It was my first time ever to use Linux so I was a little lost as to what to do to fix it, but after some poking around, I did get it working.

I went to **System > Administration > Network**.  I unchecked my default connection (mine is "Wired Connection").  I got some tooltips about losing my connection, then I just went back in and re-checked it.  Some more tooltips came up saying I'm now connected to the network.  Within 45 seconds my connection was up and running again. 

Ever since then it worked just fine.  Just seems like I sort of had to "reboot" my network connection.

Sounds like a strange fix, I know.. but it worked wonders for me, and that's the only thing I did.

---

### Post by thelemech on 2007-06-24
thank you for the responses- yet- Xp says that ethenet card not recognized - only after second reboot!!!?????? is recognized by both Ubuntu and XP PRo before live CD during live CD yet not following a second reboot?-from using live cd
maybe my ethernet controller is dying- but everything is working fine at the moment (after first reboot)
Should I pop the hood and find the exact driver for my ethernet controller-  is there even a Ubuntu equivalent?
Or is this hardware to old?

---

### Post by thelemech on 2007-06-24
Works fine on my P3 machine:D

---

### Post by thelemech on 2007-06-24
> **yabbadabbadont said:**
> Try doing a cold boot and see if it works.  i.e. poweroff, then start back up.

Cold boot worked on 4th!!! try ---for Ubuntu -XP still will not recognize ethernet controller - looks like I am off to a Windows forum - via Ubuntu!!!!!!!!!!!!!!!!
thanx for the replies.

---

