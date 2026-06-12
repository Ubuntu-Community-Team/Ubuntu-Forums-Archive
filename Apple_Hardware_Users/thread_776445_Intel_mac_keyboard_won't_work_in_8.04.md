---
title: "Intel mac keyboard won't work in 8.04"
date: 2008-04-30
forum: Apple Hardware Users
---

### Post by dusie on 2008-04-30
I have a new aluminum imac 2.4 ghz intel core duo 2 20"monitor.  I dual boot with Ubuntu and OS X. With Ubuntu 7.10 installed the keyboard worked normally.  When I upgraded to 8.04 the keyboard will only work with keys around the uiop keys acting as a keypad.         
     I can use the F5 and F6 keys to get to a console (tty5 or tty6), but then can't get back to the desktop or go to any other consoles.  The keyboard works normally in the consoles.
     I can log into the desktop using the keyboard, but then the keyboard stops working. The keyboard is the 105 key US alternative - international which is installed by default. 
     Since I upgraded from 7.10 I can use grub to boot into the older kernel.  When in the old kernel the keyboard works normally.  If I attach a standard PC keyboard, then 8.04 works normally.  The old kernel from 7.10 is 2.6.22-14-generic. The new one from 8.04 is 2.6.24-16-generic.exhibits
     The keyboard exhibits the same behavior if I boot to the Live CD for Ubuntu 8.04.

---

### Post by dusie on 2008-04-30
I found this bug report, but have not had a chance to see if it is relevant or has a solution.

[https://bugs.launchpad.net/mactel-support/+bug/201887](https://bugs.launchpad.net/mactel-support/+bug/201887)

---

### Post by cyberdork33 on 2008-04-30
> **dusie said:**
> I found this bug report, but have not had a chance to see if it is relevant or has a solution.

[https://bugs.launchpad.net/mactel-support/+bug/201887](https://bugs.launchpad.net/mactel-support/+bug/201887)
it is relevant... there is more information here:
[http://ubuntuforums.org/showthread.php?t=771151](http://ubuntuforums.org/showthread.php?t=771151)

---

### Post by dado483 on 2008-05-01
I had the same problem...the solution is really stupid!!!
Connect a usb keyboard to the macbook and push the "Block Num" button...then try the mac keyboard and voilà..!

IT WORKS NOW!

For me this procedure was working perfect!

Davide

---

### Post by Z_o-s-o on 2008-05-01
Same problem here.

I fixed mine by hitting F6

---

### Post by blurg on 2008-05-02
The trick is to hit f6 TWICE to get your letter keys back.  Furthermore don't hit the key beneath f16 - this is what turns uiop into numpad. It is a silly kernel bug introduced recently in an attempt to clear up other problems. Hopefully they'll fix it in a future kernel, in the meantime  if you search these forums you can find ways to get most of the keyboard features working as you desire them.

---

