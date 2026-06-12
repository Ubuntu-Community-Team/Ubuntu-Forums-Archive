---
title: "Samsung SCX4100 Scanner not  working"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by jcorden on 2007-10-08
My Samsung SCX4100 MultiFunction printer/scanner works just fine as a printer but I can't get the scanner to work.

I have got XSane image scanner 0.991 installed. When I attempt to scan a window opens saying "Scanning for Devices" but then immediately shuts down. I've browsed some of the existing posts but some of the suggested fixes all look a bit scary (especially seeing as the printer works just fine).

Has anyone any suggestions as to what I could check/try in order to solve this problem.

Thanks

---

### Post by wolfen69 on 2007-10-08
acccording to this: [http://www.linuxprinting.org/printer_list.cgi?make=Samsung](http://www.linuxprinting.org/printer_list.cgi?make=Samsung)  your hardware is only partially supported. you are probably out of luck with your scanner functions.

---

### Post by jcorden on 2007-10-08
I can get it working from the terminal as root using this command

sudo xscanimage

I can't get it working as a user.

Based on other posts it is something to do with the permissions on xsane (I think it is owned by root ). 

Can anyone help any further?

---

