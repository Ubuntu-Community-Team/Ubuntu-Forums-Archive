---
title: "USB Stick not detected"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by bobble991 on 2007-04-20
Hi 
quite new to linux. I have a usb stick made by integral(512mb) which is detected by windows and by earlier versions of ubuntu but feisty seems unable to find it. Ive checked all the obvious things. Any ideas what I might be doing wrong? Also does anyone know of drivers for the lexmark all in one P4350 printer. I know there isnt one specifically for linux but maybe someone has tried compatible drivers? Feisty does pick up the printer card reader but not the printer.

Thanks
Bob

---

### Post by kidders on 2007-04-21
Hi there,

> **bobble991 said:**
> Ive checked all the obvious things.What have you checked?

---

### Post by bobble991 on 2007-04-21
Ive checked that I have usb installed. Ive checked the /media folder Also I installed usbview and theres the drive as a scsi drive. It doesnt show up anywhere else though

Bob

---

### Post by kidders on 2007-04-21
Hmm...

How do the output of **mount** and **dmesg** compare, before and after the USB disk is plugged in?

---

