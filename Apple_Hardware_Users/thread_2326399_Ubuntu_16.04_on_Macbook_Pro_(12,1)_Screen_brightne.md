---
title: "Ubuntu 16.04 on Macbook Pro (12,1): Screen brightness issue"
date: 2016-05-31
forum: Apple Hardware Users
---

### Post by vishal733 on 2016-05-31
Even at the minimum brightness level as achieved by the keyboard brightness control button, the screen still retains some brightness. Anyone has a fix?

---

### Post by brendan23 on 2016-06-07
I'm having the same problem on a Macbook Pro (10,1). This worked fine under previous versions of Ubuntu, but since upgrading to 16.04, the backlight controls have no effect on actual screen brightness. Pressing them causes the on-screen brightness display to appear and adjust, but the screen backlight stays at its brightest setting.

---

### Post by brendan23 on 2016-06-07
Ok, I found a solution. Not sure if this will help you,  vishal733, but I discovered that if I boot via grub, the backlight controls don't work. However, if I boot Ubuntu directly from [rEFInd,]("http://www.rodsbooks.com/refind/") using EFI, then it works just fine. You might also try here: [https://wiki.ubuntu.com/Kernel/Debugging/Backlight](https://wiki.ubuntu.com/Kernel/Debugging/Backlight)

---

