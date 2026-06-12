---
title: "USB Problems"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by TribuS_314 on 2008-01-31
Hello.

 I have kind of an odd issue that I haven't been able to figure out or find anything on. When I plug certain usb devices like an iPod or mouse or gamepad into the usb port, Ubuntu will not detect it until the computer is rebooted, but other devices like my external HD are detected immediately.

 If anyone has any information on this it would fbe greatly appreciated.

---

### Post by neurostu on 2008-02-01
Not all usb ports are created equal. I had the same problem on my old computer in windows. I couldn't figure it out until I noticed that I would consistently plug my ipod into one usb port and my external HDD into another. Try messing around with all the different USB ports and see if something different happens.

If nothing happens try plugging in your ipod and then in the terminal type:
```
lsusb
```

---

