---
title: "live boot black screen"
date: 2011-08-24
forum: Apple Hardware Users
---

### Post by Duloc on 2011-08-24
I have a 8.2 MBP with a 1680x1050 screen and a 6490M graphics card.  I'm trying to boot from a usb stick ubuntu live.  I'm able to get to the ubuntu menu, asking to install or start live boot, but when I select live boot I get a black screen( backlight is still on but entire screen is black).  I've waited at that screen for quite some time with no luck.  I haven't seen a similar problem on the forums.  Anyone have any advice?

---

### Post by MegaLoler on 2011-08-25
You need to add the nomodeset option to the boot command. Look at the bottom of the screen for a key that allows you to edit the boot command (I can't remember what key it is) but it will bring up the command and you can just press space followed by nomodeset then press enter.

---

### Post by Duloc on 2011-08-25
Tried the nomode set.  When booting the usb-stick activity light never flashes after selecting something and the black screen comes up.  

I am able to boot from a usb-stick with the os x lion installer on it, so I'm quite unsure of the problem currently.  

I do have an ssd as the main hard drive as well, if that could cause problems.

---

