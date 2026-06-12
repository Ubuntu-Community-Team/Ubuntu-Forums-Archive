---
title: "I want to make the switch."
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by cruzer95 on 2007-09-01
Well I want to switch from windows to Ubuntu so damn bad.

The one thing keeping me back is internet. I have my drivers and everything, it finds my network, I try to connect, it says its "attempting to join the network linksys" but then it fails. It always fails.

So i'm helping someone can diagnose this problem and help me fix it.

Any help is appreciated.

---

### Post by splintercellguy on 2007-09-01
What network card do you have? Are you using ndiswrapper or the native drivers?

---

### Post by cruzer95 on 2007-09-01
I already used it and i have the driver found and installed, and it finds my network. It just wont connect.

---

### Post by alienexplorers on 2007-09-01
Are tou using wireless or hard wired card and what model is it....

---

### Post by cruzer95 on 2007-09-01
Im using wireless,  Compact Wireless G USB adapter model WUSB54GC

---

### Post by aitorcalero on 2007-09-01
Maybe you need to renew your IP address. If is the case, try to switch off your CableModem or Router, switch on again, and then in a terminal type this:
```
sudo /etc/init.d/networking restart
```
Then check that you have a valid IP address with this command:
```
ifconfig
```
Hope this helps.

---

