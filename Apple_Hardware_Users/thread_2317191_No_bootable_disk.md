---
title: "No bootable disk"
date: 2016-03-14
forum: Apple Hardware Users
---

### Post by iishowoff on 2016-03-14
Hey guys, so I am very new to Linux and I wanted to try it out. I followed [these ]("http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/")install instructions and everything went well up until install. When ever I reboot my MBP and select the Linux bootable usb I get a no bootable disk message. Anyone know how to fix/solve this?

---

### Post by Carpentr on 2016-04-13
What method did you use to burn the Ubuntu ISO onto the USB drive?

Did you use DD or UNetbootin?  If you used DD, I would try the process again after formatting the USB and deleting all of its partitions in the disk utility.

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)

If not, UNetbootin also works. I installed Ubuntu using a bootable USB on my Mid-2014 using UNetbootin.

---

### Post by Bucky Ball on 2016-04-13
> **Carpentr said:**
> Did you use DD or UNetbootin?  If you used DD, I would try the process again after formatting the USB and deleting all of its partitions in the disk utility.

dd (disk destroyer) will obliterate anything in its path so no need to prepare the USB. Be very careful with it if dd is what you're using. [mkusb]("https://help.ubuntu.com/community/mkusb") uses dd and is apparently good and a bit safer from what I've read.

---

