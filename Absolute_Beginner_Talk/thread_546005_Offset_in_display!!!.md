---
title: "Offset in display!!!"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by hiranya on 2007-09-08
Hello World,

I'm pretty much new to Linux environment and I'm absolutely new for this forum. I have installed Ubuntu 5.10 along with Windows XP and both OSs are working just fine.

However whenever I start up my PC with Ubuntu I can see a slight offset in the monitor display (to the right). I can adjust the offset from the monitor controls in the front panel of the monitor but naturally it causes an offset in the Windows XP display.

Can anybody tell me what's going on? What are the possible actions I can take?

Thanks

Best Regards,
Hiranya

---

### Post by alienexplorers on 2007-09-08
Are you running the same resolution and refresh rate in both XP & Ubuntu.  If not this can cause the problem you are having.

---

### Post by hiranya on 2007-09-20
ya that's right...I'm running on 1024x768 resolution at 60Hz on both OSs...!!!

---

### Post by nick_h on 2007-09-20
It is possible to alter the X video timings.  Have a look at this [XFree86 Video Timings HOWTO](http://tldp.org/HOWTO/XFree86-Video-Timings-HOWTO/) - section 16.1 for details.

However, this is not a beginners topic and I suggest that you maybe post in the Multimedia & Video section for advice.

---

### Post by hiranya on 2007-09-22
Thanks..changing the timing settings frim xvidtunes worked..

---

### Post by soaklord on 2007-09-22
This is going to sound really stupid, but are you using an LCD monitor?  If so, when you see the offset, turn it off an on again and see if it self corrects.  My monitor does that every time when Ubuntu loads, and it isn't slight.  Half the screen is missing.  The on/off resolves without having to go into the menu options.  Hope this helps.

---

### Post by hiranya on 2007-09-23
Well... mine is a CRT monitor. Anyway it's good to know that....as I'm thinking about getting a LCD monitor very soon. Thanks for the information

---

### Post by Roobin on 2007-09-23
I had the same problem. Are you using a nvidia graphics card? I am, and after I downloaded the driver, it all fixed itself. To downlaod, try starting Desktop Effects. If it says you need the drivers, download them. It should work after that.

---

### Post by hiranya on 2007-09-28
You are right..I have an nVidia graphics card. But the thing is I don't have an internet connection setup for my Linux installation. It's really hard to find Linux drivers for dial up modems (yeah I'm using a dial up connection).

So whatever I do it should not involve downloading stuff directly from the Internet.

---

