---
title: "Wireless Firmware Missing on iBook G4"
date: 2012-07-15
forum: Apple Hardware Users
---

### Post by abomb07 on 2012-07-15
Hello,

     I just recently installed ubuntu 12.04 on my iBook G4. When I try to connect to wifi it says firmware missing. Is there any way I can get this "firmware". It would also be helpful if I didn't have to use ethernet. Thanks in advance.

---

### Post by 2blue on 2012-07-15
You have to get a wired connection and do the updates (cable directly into a modem). It sorted its' self out on my ibook G4 as soon as I rebooted after updates. You probably have to add two lubuntu restriced packages in package manager to make it work. It's easily done, but unfortunately it looks like you need the cable, neither of my usb wireless adaptors worked on first bootup.

---

### Post by rsavage on 2012-07-15
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

---

### Post by 2blue on 2012-07-15
Thanks rsavage, I have to try that. It would make it quite a bit easier to get wirless activated at once.

---

### Post by Bucky Ball on 2012-07-15
> **2blue said:**
> It would make it quite a bit easier to get wirless activated at once.

Agreed. Catch 22, really. Easiest to plug in cable and do update, as suggested, if that's possible. ;)

---

### Post by abomb07 on 2012-07-16
> **2blue said:**
> You have to get a wired connection and do the updates (cable directly into a modem). It sorted its' self out on my ibook G4 as soon as I rebooted after updates. You probably have to add two lubuntu restriced packages in package manager to make it work. It's easily done, but unfortunately it looks like you need the cable, neither of my usb wireless adaptors worked on first bootup.

Thanks for the reply.

This also helped.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

---

