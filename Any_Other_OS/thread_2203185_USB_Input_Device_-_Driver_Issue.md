---
title: "USB Input Device - Driver Issue?"
date: 2014-02-02
forum: Any Other OS
---

### Post by Shadius on 2014-02-02
Hey everyone, 

I have a Dell Inspiron N5010 running Microsoft Windows 7 Home Premium. My issue is that the 3 USB ports aren't working anymore. I've gone into the Device Manager and tried updating the drivers, but that didn't solve the issue. Windows says it's up to date. I've tried doing a Windows Update, and that didn't work either. Please help!

---

### Post by mips on 2014-02-02
Try removing/deleting those devices in the device manager, reboot and when it picks up new hardware point it to your downloaded drivers.

---

### Post by Shadius on 2014-02-02
Tried it. Didn't work.

---

### Post by mips on 2014-02-03
Then I'm out of suggestions.

---

### Post by mörgæs on 2014-02-03
Do they work in a live boot of Buntu 13.10?

---

### Post by Shadius on 2014-02-04
Nevermind everyone. I've fixed the issue. Thanks.

---

### Post by Iowan on 2014-02-04
Perhaps you could share your solution... :)

---

### Post by Shadius on 2014-02-04
I uninstalled the drivers for each USB port one by one, including the controllers. It seems that it was the driver for the controller that was causing the issue. Windows picked up the correct dirver after that on its own.

---

