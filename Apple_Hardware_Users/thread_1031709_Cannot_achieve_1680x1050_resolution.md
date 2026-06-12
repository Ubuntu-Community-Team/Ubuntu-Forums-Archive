---
title: "Cannot achieve 1680x1050 resolution"
date: 2009-01-05
forum: Apple Hardware Users
---

### Post by jamiepgs on 2009-01-05
I currently have a Mac Mini, with Ibex installed, which is connected to an old CRT monitor. I recently got a 22" TV (Acoustic Solutions) and connected my mac to it using an HDMI to DVI cable. The TV managed to show the rEFIt boot screen, however, everything after I got a message on my TV saying "Out of Range". This is obviously a problem with the resolution, so I decided to connect my old CRT, change the resolution to something it could handle (1024x768) and then connected it back to the TV. This time it worked, however, it had a lot of over cutting, so I found my way to the Screen Resolution GUI to change it, and 1024x768 was the only option. So I added 1680x1050 (the TV's recommended resolution) to the xorg.conf file and rebooted, but I got the message again, so I put it into my CRT again however, 1680x1050 wasn't on the list of resolutions, so I added it to the xorg.conf file whilst connected to the CRT, rebooted, and lo and behold, 1680x1050 was there. Naturally, being a CRT, it adapted itself to the resolution and I connected it to the TV again, however. Ubuntu is saying the resolution is 1680x1050, but my TV is saying its 1024x768, and when I checked the Screen Resolution again, 1680x1050 was removed from the list. 

is there anywhere I am going wrong?

If there's any information you need, just ask and I will do my best to provide it.

Thanks

---

### Post by pxwpxw on 2009-01-05
Possibly the hdmi wants 1920x1080.

---

