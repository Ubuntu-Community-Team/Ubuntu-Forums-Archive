---
title: "Booting is slows"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by st33med on 2007-07-24
Whenever I boot I have it load for a few seconds, then it freezes. I hit alt-f6 then alt-f8 and it tells me something about netif trying to rename my wireless card from wlan0 to eth1, but it can't because the device is busy. It stays frozen for bout a minute then loads up nice and pretty. The only workaround I have is disable the wireless via Fn-F2, but I want to know if their is a better fix... Is their???

Also, the wireless card is a Dell 1390 WLAN. And I already have the driver for it working.

---

### Post by testube_babies on 2007-07-24
Do you use Network Manager?  If so, you can safely follow this post:
[http://ubuntuforums.org/showpost.php?p=2926155&postcount=5](http://ubuntuforums.org/showpost.php?p=2926155&postcount=5)

If it doesn't work (the Broadcom card could cause problems), you can easily undo it.

---

### Post by st33med on 2007-07-24
Thanks for telling me that. I'll try rebooting now.

---

### Post by st33med on 2007-07-25
Well that worked... Until the part where the wireless card is supposed to be recognized. I need to see if their is a way to disable the card until it has been renamed from wlan0 to eth1...

Also, I'm sure ndiswrapper is a part of this, so if I can prevent ndiswrapper renaming this, that would also help.

---

