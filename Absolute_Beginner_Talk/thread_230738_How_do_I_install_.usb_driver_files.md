---
title: "How do I install .usb driver files??"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by cheway on 2006-08-06
I have FINALLY found the right driver (apparantly) for my scanner, and I have the a file named "A2Nfw.usb" just sat on my desktop - how on Earth do I install this?

Thanks.

---

### Post by Sutekh on 2006-08-06
Well firstly I have to ask if you've tried [XSane](http://www.xsane.org/) to get your scanner working.  It worked my scanner without any intervention from me.

Is that driver you found for your scanner for Windows?  If so then there may be no way to install it on Ubuntu.

Installing XSane is easy, just search for it in Synaptic or use
```
sudo apt-get install xsane
```
from a Terminal window (Applications -> Accessories)

---

### Post by cheway on 2006-08-06
Thanks for the reply. I was up at it ALL last night, and the whole of today to get it working - in the end I had to put that .usb file in "/usr/local/share/sane/gt68xx/", gave the machine a reset, and hey presto!

Mate, I tried every possible combination of sane, xsane, that kudo (?), gt68xx one, I didn't know WHAT I was doing. 

I also had to upgrade to "libusb-0.1.8", as apparantly this version or higher is required (I could only get up to version 0.1-4 through Synaptic).

This page will also come in very handy for anyone else installing Mustek scanners (there are quite a few other ones in there as well). [http://www.meier-geinitz.de/sane/gt68xx-backend/](http://www.meier-geinitz.de/sane/gt68xx-backend/)

> Is that driver you found for your scanner for Windows? If so then there may be no way to install it on Ubuntu.

You're right about it being a Windows driver, but believe it or not, that appears to be the way to do it if your scanner doesn't "plug-and-play" as it were (If you'll excuse the Windowsism). On that page, it talks about putting in your Windows driver CD and take the .usb file off!! (I'd downloaded mine). Just shows you how adaptable Linux can be in my opinion.

Thanks again for the reply.

---

### Post by Sutekh on 2006-08-07
Well that is interesting, you learn something new everyday.

Good to hear it's all working!

---

