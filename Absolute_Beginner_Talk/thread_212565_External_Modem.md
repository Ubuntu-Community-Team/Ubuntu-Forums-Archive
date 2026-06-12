---
title: "External Modem"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by sarum on 2006-07-10
Hi, I've just bought a 2nd hand Dynalink 1456-C for my Breezy Badger. The Dynalink web site says:-
" Installing an external Dynalink Serial modem under Linux

There are 2 basic commands to link the COM port to the modem, as Linux refers to the modem as /dev/modem. Under Linux, COM1 is known as /dev/ttyS0 and COM2 is known as /dev/ttyS1.

Linux progams will use the modem as /dev/modem as default, so to create a link to your modem you must use the LN command (Link command).

To link the modem to COM1, use the command:

ln /dev/ttyS0 /dev/modem -s

To link the modem to COM2, use the command:

ln /dev/ttyS1 /dev/modem -s"

I've typed in sudo then as above; press enter and I get the answer:- Ln '/dev/modem' exists. The modem is connected up and plugged in, and turned on (green and red lights show). But I don't know what to do next. Firefox is off line.Please help and thanks Sarum.

---

### Post by lordlollo on 2006-07-10
Just go to

System -> Adiministration -> Networking

enter your root password, and configure the internet connection. Note that you can try to have your modem be automatically detected by your machine. Then, you just have to fill the forms with data provided by your isp.

Cheers.

---

### Post by sarum on 2006-07-10
Thanks for you reply. I shall try it this evening.
Cheers Sarum

---

