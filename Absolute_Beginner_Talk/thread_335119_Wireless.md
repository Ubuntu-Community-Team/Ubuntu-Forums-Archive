---
title: "Wireless?"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by Jyrenth on 2007-01-09
I'm on a college campus that uses encryption, specifically I need to change these things:
# Encryption: WPA Radius with TKIP key exchange
# Authentication: 802.1x with PEAP and MSCHAPv2
Which don't seem to be options in the wireless manager.  What should I use?

---

### Post by yager on 2007-01-10
Check this link for some help.

[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)

Before you install wpa_supplicant, check the package manager to see if it is already configured on your system.

There were some other pages on this Google search that may also point you in the right direction.

[http://www.google.com/search?hl=en&lr=&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=Cd&q=PEAP+Linux+Wireless+WPA&btnG=Search](http://www.google.com/search?hl=en&lr=&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=Cd&q=PEAP+Linux+Wireless+WPA&btnG=Search)

---

### Post by Atomic Dog on 2007-01-10
If you're running Edgy (6.10) and have a working wireless (which I assume works already) then I would download Network Manager.  You can install it easily by clicking on Applications-->Add/Remove then select Network Manager from the Internet tab on the left.  This will very likely make it possible for you to connect to your school's wireless.

---

