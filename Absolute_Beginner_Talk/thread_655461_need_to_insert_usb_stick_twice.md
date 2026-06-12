---
title: "need to insert usb stick twice"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by kaston on 2008-01-01
for some reason, whenever i insert my usb stick into my laptop (toshiba satellite A100 VA9), it is not immediately recognized.  i always need to take it out and reinsert it a second time in order to get it on the desktop.  any way to fix this?

---

### Post by mmb1 on 2008-01-01
What brand is it and how old?  Flash drives lose some of their functionality over time.

---

### Post by kaston on 2008-01-01
it's less than a month old.  it's a PNY 8GB USB stick.  i'm pretty sure it isn't the USB stick though because i don't have this problem when using it in other non-ubuntu computers (like win xp and mac)

---

### Post by mmb1 on 2008-01-01
Okay, thanks for the info.  Go into synaptic and make sure you have the "usbutils" package properly installed.

---

### Post by kaston on 2008-01-01
yep, usbutils is already installed

---

### Post by az on 2008-01-01
> **kaston said:**
> for some reason, whenever i insert my usb stick into my laptop (toshiba satellite A100 VA9), it is not immediately recognized.  i always need to take it out and reinsert it a second time in order to get it on the desktop.  any way to fix this?

Open the log tool and post the output of /var/log/messages when you insert the drive.  Try getting any messages from both the times when it is immediately mounted and not.

Start viewing the logs before you insert the thing.

---

