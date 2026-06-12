---
title: "Broadcom restart problem..."
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by thekylehome@gmail.com on 2008-02-19
Okay, here is my problem...

I have to go into restricted drivers and uninstall my broadcom 43xx chipset and then reinstall it through the restricted drivers, to get wireless! Even more, I have to do this every time I start up the computer!
I have the identical problem as this user did here: [http://ubuntuforums.org/showthread.php?t=653896](http://ubuntuforums.org/showthread.php?t=653896)

Any Ideas on how to resolve this???

---

### Post by thekylehome@gmail.com on 2008-02-19
Okay, for those of you who have had the same problem... here is a temporary fix---

supposing you have the drivers/firmware installed, go System>Preferences>Sessions. Click "Add" and then under Command type: gksudo modprobe bcm43xx  write whatever best fits you under the "Name" and "Comment." 
Your done! Just be sure to restart...

Hope this saves someone... I needed this A LOT sooner!!!

STAFF: you might consider putting this as a sticky under "networking and wireless." Just an idea... know it would have saved me lots of time!

---

