---
title: "How do I bind the device"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by abrand888 on 2007-06-25
I am using 7.04 and believe I am getting up to the final part of making ndiswrapper worked with a USB Lan driver device made by Engenius. I did everything including compiling ndiswrapper.

The last thing I did was   cat /etc/modprobe.d/ndiswrapper and I got the line  alias wlan0 ndiswrapper.

How can I get the network to see the device so I can go out to the Internet ?

Arthur

---

### Post by swoll1980 on 2007-06-25
Did you try duct tape that fixes everything.  :D

---

### Post by bluknight on 2007-06-25
> **swoll1980 said:**
> Did you try duct tape that fixes everything.  :D

If I guess right he must be a lisp programmer before.
Anyway after getting ifconfig wlan0 to show wireless present you should (as root) do:
dhclient wlan0
(or)
dhcpcd wlan0
(then)
ping google.com
to check that it has been connected

---

### Post by swoll1980 on 2007-06-25
[QUOTE=bluknight;2914117]If I guess right he must be a lisp programmer before.

Hey you forgot about Fortran didn't you

---

