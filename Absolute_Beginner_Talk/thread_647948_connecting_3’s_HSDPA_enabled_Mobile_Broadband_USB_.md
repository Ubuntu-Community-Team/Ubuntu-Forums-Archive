---
title: "connecting 3’s HSDPA enabled Mobile Broadband USB Modem"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by nichanson on 2007-12-22
Hi
I'm from Australia and have an HSDPA modem with the mobile network '3'. I'm wondering how to get it working in Ubuntu 7.10 as they only give instructions for windows and mac. The modem is recognised as a cd drive and pops up on the desktop when I plug in the modem and they provide the following information in there windows guide:

Profile name: 3 Mobile Broadband
Authentification number: *99#
Username/Password: [left blank]
DNS Setting: [left blank]
APN: static & “3netaccess”
IP Settings: [left blank]
Authentication Protocol: CHAP
WINS Settings: [left blank]

but I don't know where to input these in?????
Thanks for anyone who can help
Nick

---

### Post by waynefoutz on 2007-12-23
here is what I did to get mine working, first you open up synaptic, assuming you have another means of connecting to the internet, and install gnome-ppp. this is only temporary though, because gnome-ppp is broken in 7.10 and it will not dock after the modem connects, but install it any way. in the setup in gnome-ppp you can tell it to autodetect the modem. it came up /dev/ttyUSB0 on my laptop. write whatever results it gives down. Now, go back to synaptic, uninstall gnome-ppp and install KPPP. It is a similar program, but much better I think. feed all the info into kpp's fields, log in, phone number, and the info you got from the autodetect. you should be good to go, I was anyway.

---

### Post by idefixuk on 2008-03-10
Installed Ubuntu 7.10 on my laptop (ditched Vista for good!) and still got lot of problems although I love it. I bought a 3 usb modem for mobile broadband (threestore.three.co.uk/broadband/). While it works on the laptop of a friend that has xandros installed, I cannot install it on mine. My laptop is a Toshiba Portege. I followed waynefoutz instructions but still not connection. Any other suggestion please? None of my friends know a thing about Linux. :-(

---

