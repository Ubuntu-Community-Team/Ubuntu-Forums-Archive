---
title: "Sierra Wireless Ac595U with ubuntu ??"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by zurk on 2007-08-27
How do i use the sierra wirless ac59u usb modem with ubuntu ?? i have it activated with windows.

---

### Post by Inxsible on 2007-08-27
This guide is for Voyager 105 USB Modem, but you might wanna have a look at it and see if it works for you. Here's the  [link]("http://www.jarviser.co.uk/jarviser/linuxusb.html")

---

### Post by hector_g on 2007-09-09
I found this guide from Sprint:  [http://www4.sprint.com/pcsbusiness/d...etup_Guide.pdf](http://www4.sprint.com/pcsbusiness/d...etup_Guide.pdf)) I'm trying to setup my air card too.  Let me know if you have any luck.

---

### Post by cmccartin on 2007-11-29
Check out [[COLOR="Red"]_this_[/COLOR]]("http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601") link to sierra wireless.. I got my AC595U working with kernel 2.6.22.. The sierra module is distributed with this kernel version, so you don't need to compile the module. (check 'modinfo sierra' )

Three devices will be created when you insert the modem (ttyUSB0, ttyUSB1, ttyUSB2), but the actual device to use is /dev/ttyUSB0

It acts just like a regular serial device - you can issue AT commands, etc

Hope this helps!

---

### Post by bengar on 2007-12-11
I'm very unhappy with the bad service of my Internet Provider, I ear about the Sierra Wireless from Sprint.A good friend has one, I tried plug in but Gutsy does not recognize it. But later I did a search here and found yours talking about it. I did a "modinfo sierra" and this is what show me.
[CENTER][IMG]http://i15.tinypic.com/85udc00.png[/IMG][/CENTER]

If I have the driver, what next I need to do to make the sierra start work? thanks in advance, and sorry to my ignorance.

---

### Post by cmccartin on 2007-12-19
Which device are you using?

Can you post the output of 'lsusb'? This will show the vendor and product id of the device.

---

