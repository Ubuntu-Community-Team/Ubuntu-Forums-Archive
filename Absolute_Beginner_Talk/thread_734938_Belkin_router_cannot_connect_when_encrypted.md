---
title: "Belkin router cannot connect when encrypted"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by gewitty on 2008-03-25
I'm having a problem getting encryption to work with Ubuntu. If I set up my Belkin router to use WPA and enter a passphrase, I find that my Asus eee, which runs Xandros, connects immediately. However, the Ubuntu machines will not connect whatever I try, so I have to leave the network unsecured.

Has anyone any idea as to why Xandros works and Ubuntu doesn't?

---

### Post by Golem XIV on 2008-03-25
Most probably it's a question of the wireless driver badly/not supporting WPA.  I had the same problem with 2 laptops, on the HP (Broadcomm 43xx) I had to remove the restricted driver and replace it with ndiswrapper, and on a Dell I had to replace network-manager with wicd.

Let us know what your wireless chipset is and what drivers you're using so that we can help you find a solution.

---

### Post by gewitty on 2008-03-25
I'm using Belkin F5D6050 adapters, which I believe use the  Atmel AT76C503A-Accton USB 11b WLAN chipset. The w/router is a Belkin F5D7632-4.

Not sure where to find info on the drivers.

---

