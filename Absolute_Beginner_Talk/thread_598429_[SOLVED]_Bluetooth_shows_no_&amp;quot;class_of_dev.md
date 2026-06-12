---
title: "[SOLVED] Bluetooth shows no &amp;quot;class of device&amp;quot;"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by lazyart on 2007-10-31
I'm having trouble connecting devices via bluetooth.  Somehow my gutsy laptop is not sending a device class.  It used to let me set it to laptop/desktop, but now that option is greyed out.  Because of this I can't connect my PDA to it.

When scoping out the area from a windows desktop, instead of a type of device (phone, pda, computer) it says Unknown Major(0), Minor (0).  How do I set these values?

---

### Post by lazyart on 2007-10-31
Resolved:```
sudo hciconfig hci0 class 0x52010C
``` using code generated from [http://bluetooth-pentest.narod.ru/software/bluetooth_class_of_device-service_generator.html](http://bluetooth-pentest.narod.ru/software/bluetooth_class_of_device-service_generator.html)

---

