---
title: "Printer"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by X-Microsoft on 2007-06-13
I cannot get my Lexmark X1185 printer to work with Ubuntu. I am thinking about buying a Kodak EASYSHARE 5300 All-in-One Printer but would like to know if anyone knows if this works with Ubuntu.

---

### Post by reclusivemonkey on 2007-06-13
[http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi)

List and recommendations. Hope this helps =]

Also, I will mention that for photo printing, its often cheaper to get your pictures printed online and mailed to you now, rather than forking out for colour inks and photo paper.

---

### Post by X-Microsoft on 2007-06-13
Ok....I have no idea of what I am supposed to do.

---

### Post by reclusivemonkey on 2007-06-14
Look at the website. Search to see if the printer you want is supported. If not, buy one of the recommendations.

---

### Post by deadlikeoscar on 2007-06-14
Try this first:

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters")

Note: I have a Dell AIO A940 (Rebranded Lexmark X1150 and a similar method worked for me and I can print in color as well but sane will not allow me to scan with it.

---

### Post by X-Microsoft on 2007-06-14
ok...........when i try to do the following, it asks for Password. It won't let me type anything.

2. Make sure you have installed the following packages

sudo apt-get install libstdc++5 alien

Finally getting somewhere until this.

---

### Post by ramjet_1953 on 2007-06-14
Lexmark printers are not very Linux friendly, as Lexmark do not release open source drivers, or release firmaware, or hardware info, so that anyone else can write a driver.

As far as new printers are concerned, I suggest that you buy HP.

Why? Because HP actively support Linux and provide drivers.

Regards,
Roger :cool:

---

### Post by w4ett on 2007-06-14
As a security measure, your password characters are completely invisible in the terminal.  Just type the P/W normally and press <enter>

---

### Post by X-Microsoft on 2007-06-15
Well.......I got my printer installed now and it does show up but still won't print. Just sits there saying printer ready.

---

### Post by deadlikeoscar on 2007-06-15
open a terminal and try sudo /etc/init.d/cupsys restart

---

### Post by X-Microsoft on 2007-06-15
Did as you said but still won't print anything.

---

### Post by deadlikeoscar on 2007-06-16
It was supposed to be cupsys...read my edited post. Sorry, I was really tired at the time.:D

---

### Post by ant1060 on 2008-07-12
Hi! Have you tried this :
[http://onlyubuntu.blogspot.com/2008/05/howto-setup-lexmark-z55-printer-in.html](http://onlyubuntu.blogspot.com/2008/05/howto-setup-lexmark-z55-printer-in.html)
I finally got my Dell A940 = Lexmark x5150 working after waiting about three years!
Good luck :)

---

