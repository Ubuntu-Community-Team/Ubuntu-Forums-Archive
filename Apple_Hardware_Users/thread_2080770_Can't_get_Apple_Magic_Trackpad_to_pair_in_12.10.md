---
title: "Can't get Apple Magic Trackpad to pair in 12.10"
date: 2012-11-04
forum: Apple Hardware Users
---

### Post by teranine on 2012-11-04
It used to work in 11.10 quite nicely and paired fine.  Now, after attempting to pair, I get this error message in the "Bluetooth New Device Setup" dialog: "Setting up 'Apple Wireless Trackpad' failed".  I've tried all methods of pin options, from using the fixed pin of '0000', to using "Automatic PIN selection", trying the other fixed pin options of '1111' and '1234'.  Sometimes, the during the pairing process, the dialog screen will ask me to enter a 6 digit number, which I do on the keyboard.  This does not work either and sometimes fails even before I've finished typing the 6 digits.  

The trackpad is identified correctly on the "Device Search" dialog, but afterwards, pairing attempts always fail.  Have also tried rebooting the OS to no avail.

I currently using an Apple Wireless Keyboard and Apple Wireless Magic Mouse without issue.  Both have paired fine and work well.  Was hoping to try out the trackpad again in 12.10.  Perhaps I need to disable the Magic Mouse to get the Magic Trackpad working?

System is completely updated.

---

### Post by debb1046 on 2012-11-24
I saw exactly the same symptoms. Finally managed to pair the trackpad using blueman-manager (install package blueman from repos) instead of the standard bluetooth applet.

---

### Post by tebeka on 2012-11-27
Same problem here. Ubuntu 12.10 x64

---

### Post by howefield on 2012-11-27
Thread moved to the "*Apple Users*" forum.

---

### Post by nh2 on 2013-05-23
Please try the workaround I describe in post #6 on [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/618838](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/618838).

---

