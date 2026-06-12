---
title: "Apple Keyboard and F Keys?"
date: 2017-12-02
forum: Apple Hardware Users
---

### Post by sterator on 2017-12-02
I experimented with LXDE and found a keyboard assigner that gave/restored F key functionality, including things like controlling audio volume.

Now that I'm back in Cinnamon, I see no such ability. Is something actually available for Mac Keyboard users to assign functionallity to our keyboards?

Thank you!

---

### Post by kevin160 on 2017-12-12
Is it possible that your keyboard assignments are just flipped?  Does pressing fn-F12 instead of just F12 increase volume?  If so, try setting the hid_apple fnmode in your mod probe settings:
 
To get Volume-up when you press F12 and "F12" when you press fn-F12, add 

options hid_apple fnmode=1

to  /etc/modprobe.d/hid_apple.conf and then do an update-initramfs -u

fnmode=1 will give you Volume-up when you press F12 and "F12" when you press fn-F12.

Also see [https://help.ubuntu.com/community/AppleKeyboard](https://help.ubuntu.com/community/AppleKeyboard) which is a bit out of date but still helpful.

---

