---
title: "Rt73 (2501) Usb Tp-link Tl-w321g"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by ronamin on 2008-02-08
hi all
i installed ubuntu twice on same computer
once it recognized my usb-wifi automatically but was not so stable (connection lost)
then i reinstalled the ubuntu (first install was for playing and checking)
now it simply not recognizing it
is there a good guide to install this usb-adapter?
something written for 7.10?

---

### Post by spydon on 2008-02-08
Did you have it plugged in when you did it the first time and not the other or something like that?

If you have a driver cd it should work fine if you use ndiswrapper, [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

But be sure that it detects it first, write ```
lsusb
``` in the terminal and copy the output here.

---

