---
title: "Graphics Card Problems"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by rbrittner on 2008-02-21
Hello, I recently installed a graphics card update that was pushed out and now after a reboot my machine doesn't recognise my video card, It did however give me the option to boot in low resolution or pick my card, I accidently picked the wrong card and now when it boots I can't read sh!t.  Can someone help me on how to boot in recovery mode and then what I need to type in order to get the generic Video card at low resoltuion to display.  That way I can go in and install the correct drivers for my ATI card.  I guess I figured that if I picked the wrong one there would be an option to boot in "Safe Mode" as per windows......oops. :)

Thanks

---

### Post by S15_88 on 2008-02-21
boot to recovery mode and type: sudo dpkg-reconfigure xserver-xorg

---

### Post by rbrittner on 2008-02-21
Ok thank you, i'll give it a try when I get home from work tonight, Thanks again

---

### Post by S15_88 on 2008-02-21
no problem, that will let you pick a generic driver, screen resolution, and stuff then once you got all that fixed up you can do what you got to do to get your specs working.

---

