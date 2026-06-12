---
title: "How to: External Apple USB modem + MacBookPro + Ubuntu 8.04 or 8.10?"
date: 2008-10-08
forum: Apple Hardware Users
---

### Post by tp42 on 2008-10-08
Hi there,
I am looking for a solution to connect my external Apple USB modem (56k, dial up) to Ubuntu 0.04 or Ubuntu 8.10 on my MacBook Pro Core2Duo. I searched on the web and the English and German speaking Ubuntu forums for a solution but with no sufficient results yet. The best I could find was "[Driver for Apple USB modem 05ac:1401]("http://www.linux-archive.org/debian-laptop/145944-driver-apple-usb-modem-05ac-1401-a.html")"
Though, at the moment  I am somewhat stuck with this task. However, 
a)	is it even possible to connect the Apple USB modem to my Ubuntu MacBook, .i.e. is there some sort of cook book for that known? 
b)	if there is no solution for a), is there an external UBS modem (manufacturer, type?) around which reportedly works with Ubuntu on a MacBook Pro Core2Duo.?
Any hint would be greatly appreciated?

With kind regards: Thomas

---

### Post by mikeygstl on 2008-12-23
Well, I just plugged it into my debian based slug, and immediately got the following:

```

usb 1-1: new full speed USB device using ohci_hcd and address 3
usb 1-1: configuration #1 chosen from 1 choice
usbcore: registered new driver snd-usb-audio

```

Now, under Mac OSX, with Quickterm, I have been able to find out the following:

```

ATI1
Apple Version 1.5.9
OK
ATI2
OK
ATI3
Motorola SM56 USB 1.5.9
OK
ATI7
Motorola SM56 USB Fax Modem
OK

```

---

