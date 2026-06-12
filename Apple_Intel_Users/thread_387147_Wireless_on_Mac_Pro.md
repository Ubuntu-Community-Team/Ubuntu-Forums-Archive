---
title: "Wireless on Mac Pro?"
date: 2007-03-17
forum: Apple Intel Users
---

### Post by resistor2004 on 2007-03-17
Has anyone successfully gotten wireless working on a Mac Pro?  I've tried using ndiswrapper with the bcmwl5 driver to no avail.  Any suggestions?

---

### Post by cyberdork33 on 2007-03-18
are you using the driver from the boot camp cd? I could not get it working with other drivers for the broadcom chipset on my iMac

---

### Post by resistor2004 on 2007-03-23
Yes, it's the driver on the bootcamp CD.

---

### Post by resistor2004 on 2007-04-02
*bump*

Has *nobody* gotten this to work?

---

### Post by cyberdork33 on 2007-04-02
As far as I can tell there are not many people running this on a Mac Pro. If the driver you have from the BootCamp CD and ndiswrapper is not working then you are kind of stuck. After installing the driver, what do you get when you do:

```
ndiswrapper -l
```

---

### Post by resistor2004 on 2007-04-02
Upgrading to a new ndiswrapper and kernel (by downloading and transferring from another machine) got it going!

Thanks, though!

---

### Post by Terry Jones on 2007-04-09
I have gotten wirless to work on a mac book pro 17 Inch using ubuntu and  kubuntu with no extra software and I was able to connect my home network which had wep enacted and to an open network at southwest tn community college 
Which desktop enviroment are you using? The insructions will vary with desktop enviroment.

---

### Post by cyberdork33 on 2007-04-09
He is talking about Mac Pro, not Macbook Pro

---

### Post by Terry Jones on 2007-04-09
All macs are generally the same now. What is the desktop enviroment you are trying to use

---

### Post by cyberdork33 on 2007-04-10
Actually there are several different wireless chipsets just in the Core2Duo Macs (at least 1 Broadcom and 2 different Atheros). And if yours worked out of the box, then my guess is you have one of the compatible atheros chipsets. He is using a broadcom chipset, hence the need for ndiswrapper.

Besides, he already got it working, it was an ndiswrapper issue.

---

