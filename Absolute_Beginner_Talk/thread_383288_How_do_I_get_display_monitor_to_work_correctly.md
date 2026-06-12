---
title: "How do I get display monitor to work correctly?"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by randall.hoag on 2007-03-13
I just installed Ubuntu 6.10 on an old Dell Inspiron Laptop.  Everything works fine except the laptop monitor.  The screen is split into 3 columns making it almost impossible to use.  If I plug in a separate display monitor to the laptop, I can at least get a single screen, but it is greatly reduced in size in the middle of the overall screen.  I only have 2 options for screen resolution:  600 x 600 and 600 x 480. Your help would be much appreciated.   Randy

---

### Post by Jussi Kukkonen on 2007-03-13
> **randall.hoag said:**
> I just installed Ubuntu 6.10 on an old Dell Inspiron Laptop.  Everything works fine except the laptop monitor.  The screen is split into 3 columns making it almost impossible to use.  If I plug in a separate display monitor to the laptop, I can at least get a single screen, but it is greatly reduced in size in the middle of the overall screen.  I only have 2 options for screen resolution:  600 x 600 and 600 x 480. Your help would be much appreciated.   Randy

If you can bear using the command line, run *sudo dpkg-reconfigure xserver-xorg*, and answer the questions as well as you can. Then restart X with ctrl-alt-backspace

---

