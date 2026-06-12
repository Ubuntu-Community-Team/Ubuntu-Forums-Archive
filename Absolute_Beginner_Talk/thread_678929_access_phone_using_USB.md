---
title: "access phone using USB"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by placo on 2008-01-26
Hi there!

I run solo ubuntu half a year now, very pleased. But after buying my gsm samsung sgh-u100 i discovered that i cannot acces the phone using USB with ubuntu.

Strange, i thought it would be easy with ubuntu!

I concider myself as a test-user with effort, but have not found a solution for this yet, and cannot find decent information about the subject.

Anyone?

---

### Post by finer recliner on 2008-01-26
you'll probably need a special application to access files on your phone (i.e. bitpim). and that application may need to be given permissions to use the USB ports:

[http://www.bitpim.org/help/](http://www.bitpim.org/help/)
Reference > USB > Linux USB setup

---

### Post by ExpatPaul on 2008-01-26
I had the same issue with my Nokia and ended up using OpenOBEX to access it. There's a good HowTo (it worked for me) at [matallo.org]("http://matallo.org/how-tos/nokia-6680-ubuntu-with-dku-2-usb-cable/")

---

### Post by placo on 2008-01-28
tried both of them and installed virtual box, installing xp for long time in it. But no success there either, the USB controller has some problems connecting the USB-phone. I have no bluetooth on my machine. And the samsung studio doesn't provide the issues i would like to counter. Big nothing so far...

---

### Post by rab4567 on 2008-02-10
Hey I've been there I have a Samsung sch-u740

1.) Go to bitpim.org download the latest debian pacage version 1.0.5.0

2.) Plug in the usb cable to your phone then go to applications> accessories> terminal type lsusb and enter. You should see a string of driver listed thats a good sign.

3.)Then type in terminal sudo bitpim enter then your password and you should get a conformation box stating it recognizes your phone then type in your name and phone model.

Good Luck

---

