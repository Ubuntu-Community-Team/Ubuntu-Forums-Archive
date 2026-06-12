---
title: "Braodcom Wireless"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by jbaerbock on 2007-03-16
I am rather new to Ubuntu and was wondering how to configer my broadcom wireless card to work with Ubuntu. At the moment when I try to activate it, it sits there with the bar going back and forth for awhile then says it is activated but it has yet to work. Wired network through the same network works fine though. Anyone know of any simple easy to follow ways of setting up my internal Broadcom Wireless in my HP zv6000? 
Also how could I find out information about said card, is there any command I could run in terminal that would show card info? Thanks.

---

### Post by SactoBob on 2007-03-16
lspci should include data on the chip if it is on the pci bus.
lsusb if on the usb bus.

iwconfig should tell you about the status of the connection, and you can use some switches on that command to find out more.

---

### Post by jbaerbock on 2007-03-16
Ok thanks will definitely try that out.

---

