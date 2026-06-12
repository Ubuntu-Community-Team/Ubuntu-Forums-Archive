---
title: "Need help with ndiswrapper."
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by ananchai on 2006-02-14
I just successfully installed ndiswrapper-utils from Sypnatic. I tried the following commands, and I got error messages. Please help and thanks in advance. 

[B]ananchai@ubuntu:~/Desktop/Linksys_Driver/WUSB11v4_08272004/Drivers$ sudo ndiswrapper -e wusb11v4
ananchai@ubuntu:~/Desktop/Linksys_Driver/WUSB11v4_08272004/Drivers$ sudo ndiswrapper -i WUSB11v4.inf
Installing wusb11v4
Parse error in inf. Unable to find section @mdusb.out
ananchai@ubuntu:~/Desktop/Linksys_Driver/WUSB11v4_08272004/Drivers$[/B]

---

### Post by palomar on 2006-02-14
I think it's not a good driver to work with ndiswrapper. E.g. in the documentation is said it often won't work if you use the drivers form the CD. T

So try if you can find another (newer/older) driver.

---

