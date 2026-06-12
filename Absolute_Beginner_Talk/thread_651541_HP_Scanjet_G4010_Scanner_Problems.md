---
title: "HP Scanjet G4010 Scanner Problems"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by hoffmannick on 2007-12-27
Hello, I can't seem to get my scanner working correctly (or at all for that matter)

The model is an HP Scanjet G4010

running the following will give me this information 
```
~# sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x4505 [HP Scanjet G4000 Photo series], chip=GL841) at libusb:006:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```

So it claims to find the scanner, but when I start SANE it will not recognize that a scanner is connected.  Is there any other programs or ways that I can connect this scanner to ubuntu?

Thanks for your help!
-Nick

---

### Post by blueridgedog on 2007-12-28
Have you tried Xsane as a front end to sane?

---

### Post by hoffmannick on 2007-12-28
Yeah, I've tried Xsane as well as Kooka.  Xsane just lets me know that it can't find a scanner which is odd because sane-find-scanner seems to locate one.

I've done some hunting for particular drivers on source forge with no luck.

I have not found any solution to this problem at all.  I've been working diligently on finding a solution.

Are there any other Ubuntu scanning utilities that may have support for my scanner?

---

### Post by blueridgedog on 2007-12-28
It appears that the sane site reports that scanner as unsupported:

[http://www.sane-project.org/cgi-bin/driver.pl?manu=Hewlett-Packard&model=G4000&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=Hewlett-Packard&model=G4000&bus=any&v=&p=)

The sane-find-scanner will find most scanners, even those that are not supported.  The question of support pertains, in this case, pertains to getting information from the manufacturer.

---

### Post by ramnarayan on 2008-02-07
HI

Was checking to see if there are any new solutions to getting this scanner - HP Scanjet G4010 Photo Scanner-  to work

or is there any other equivalent model (of any other company) that works under Linux (Ubuntu)

thanks
ram
India

---

### Post by hoffmannick on 2008-02-12
No solutions have been found yet, or at least not to my knowledge.

---

### Post by impeteperry on 2008-03-14
Hi. I have a G4010 which I can only use on XP or Vista. I have not been able to find anywhere an equivalent scanner that supports linux. I suppect HP has sold its soul to Microsoft!. This is an issue that should be investagated for legal action. Any thoughts.

---

### Post by hoffmannick on 2008-03-15
I gave up the quest trying to get the G4010 working. 

HP hasn't made my bad list yet.  I recently saved up the money, and bought a Photosmart_C7200 and it works perfectly in Ubuntu.

---

