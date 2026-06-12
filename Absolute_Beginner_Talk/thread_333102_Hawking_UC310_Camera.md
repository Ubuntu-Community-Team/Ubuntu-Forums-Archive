---
title: "Hawking UC310 Camera"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by garya on 2007-01-06
Hi all--

I have an old Compaq Armada laptop, PII, 266 MHZ, 224 mb (or so) RAM.  I installed Xubuntu 6.06 LTS, and on the whole it works pretty well.  

My brother gave me a Hawking UC310 Hawkeye USB Camera.  I plug it in on startup but nothing shows up on the desktop.  I can't find Linux drivers for it.  Is there any way to get to work with this setup?  

gary

---

### Post by Ergo on 2007-01-06
I'm sorry to say . . . if it is not in this list, it's not supported YET.

[http://www.qbik.ch/usb/devices/search_res.php?pattern=webcam](http://www.qbik.ch/usb/devices/search_res.php?pattern=webcam)

You may be able to search the web and find that it shares a driver with some other cam that is supported.  When checking for hardware, does it show up as being recognized as a USB device?

---

### Post by garya on 2007-01-07
> **Ergo said:**
> I'm sorry to say . . . if it is not in this list, it's not supported YET.

[http://www.qbik.ch/usb/devices/search_res.php?pattern=webcam](http://www.qbik.ch/usb/devices/search_res.php?pattern=webcam)

You may be able to search the web and find that it shares a driver with some other cam that is supported.  When checking for hardware, does it show up as being recognized as a USB device?

It's not on the list, so I guess I'll put it away for now.

How do I check for hardware?  The green led on the camera lights up, so I'm guessing it's recognized as a USB device.

---

### Post by garya on 2007-01-13
Anybody have any advice?

---

### Post by garya on 2007-01-22
> **Ergo said:**
> I'm sorry to say . . . if it is not in this list, it's not supported YET.

[http://www.qbik.ch/usb/devices/search_res.php?pattern=webcam](http://www.qbik.ch/usb/devices/search_res.php?pattern=webcam)

You may be able to search the web and find that it shares a driver with some other cam that is supported.  When checking for hardware, does it show up as being recognized as a USB device?

I did some more research, and it turns out the camera uses the ov511 driver.  See [http://ovcam.org/ov511/install.html]("http://ovcam.org/ov511/install.html").

 Much to my surprise I found the driver already installed.  I went to synaptic, typed in webcam in search, and tried a few programs.  Camstreams seems to work very well with no setup involved. 

However, the only way to run the program is by choosing it through run program in the applications menu.  Is there any way to get it into the the drop down for applications?

Gary

---

