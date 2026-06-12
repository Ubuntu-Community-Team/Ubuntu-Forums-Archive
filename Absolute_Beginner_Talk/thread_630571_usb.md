---
title: "usb?"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by HappyEisentrout on 2007-12-03
I just installed Ubuntu and I cant get my usb port to work.  Any ideas?

---

### Post by Het Irv on 2007-12-03
Which Version of Ubuntu?
What Kind of Computer is it?
Have you run the Updates?

---

### Post by HappyEisentrout on 2007-12-03
I'm running Gutsy Gibbon on a Fujitsu Lifebook E362 and and I have installed all the updates that I know of.

---

### Post by drs305 on 2007-12-03
The first place I'd look is System, Preferences, Removable Drives & Media Preferences to ensure automounting is enabled.

---

### Post by philinux on 2007-12-03
type 

[FONT="Times New Roman"]lsusb[/FONT] 

in the terminal and post the results.

---

### Post by HappyEisentrout on 2007-12-03
Bus 001 Device 001: ID 0000:0000

---

### Post by philinux on 2007-12-03
Try a system restart. Especially if you had a HAL error.

---

### Post by Sarteck on 2007-12-03
Not sure if it would help, but I had problems getting my camera memory card working until I ran **sudo apt-get install usbmount**

---

### Post by philinux on 2007-12-03
> **Sarteck said:**
> Not sure if it would help, but I had problems getting my camera memory card working until I ran **sudo apt-get install usbmount**

Strange that different people have problems like this. Usbmount is not installed on my system yet my pendrive mounted first time.

---

### Post by Sarteck on 2007-12-03
> **philinux said:**
> Strange that different people have problems like this. Usbmount is not installed on my system yet my pendrive mounted first time.It was actually your link in your sig that pointed me in the right direction, with that.  Heh.

But I'm assuming it might be because of different hardware manufacturers...  Like my USB 13-in-one memory card reader (pre-installed on the Dell) was made by the TEAC Coorporation, but many others I've seen are... what was it... RealTek, maybe?  All I know is that, before having my problems, I thought USB was USB, and it didn't matter how it connected or who connected it. XD  Boy was I wrong.

---

