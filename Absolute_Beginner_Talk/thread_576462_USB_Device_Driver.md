---
title: "USB Device Driver"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by jvogel on 2007-10-15
I am new to Linux.  I have been programming for over 15 years and at my new job I am to write a driver for a barcode reader attached to are system via USB.

The barcode reader registers as a keyboard device.  We are looking to have more than one of these connected to the device at anyone time.

I am trying to write a user space device driver which will know, amoung other things, when a barcode reader is connected/disconnected  to or from our unit, when and which device has scanned (read) a barcode, and to send messages to the barcode reader.

I look forward to any help that can be given to me and any other suggestions on how this can be done if not by a user space device driver.

Sincerely,
John Vogel

---

