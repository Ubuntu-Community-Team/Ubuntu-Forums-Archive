---
title: "[SOLVED] XSane Image Scanner"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by joeycbulk on 2007-03-16
How do I configure my xsane scan image? 
An error occurs every time I try to scan. The error says 
```
Error: Failed to open device `hpaio:/usb/psc_1200_series?serial=MY3C1F20837L': Error during device I/O.
```

I have a printer installed via cupsys. My printer has a built in scanner, I was able to print but I'm not able to scan images. I'm using the 6.10 version of ubuntu.

```

Description: HP psc 1200 series
Location: Local Printer
Make and Model: HP PSC 1210 Foomatic/hpijs (recommended)
Printer State: idle, accepting jobs, published.
Device URI: hp:/usb/psc_1200_series?serial=MY3C1F20837L

```

---

### Post by eljalill on 2007-03-16
Do you have the hplip package installed?
I think that is what you need.

---

### Post by rkh on 2007-03-16
According to the HPLIP folks your scanner should work:

[http://hplip.sourceforge.net/supported_devices/inkjet_aio.html](http://hplip.sourceforge.net/supported_devices/inkjet_aio.html)

Is the psc 1200 the same thing as the photosmart 1200? If it is the sane folks say it isn't supported:

[http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-HEWLETT-PACKARD](http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-HEWLETT-PACKARD)

I'd suggest making sure you have the latest version of hplip -the version in the edgy repositories is a few months older and wasn't very reliable for scanning on my laserjet 3020. The installer for this version worked quite well for me:

[http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

---

### Post by joeycbulk on 2007-03-18
I have hplip 1.6.9-0ubuntu0 installed already. The scanner is still not working

---

### Post by rkh on 2007-03-18
If the psc 1200 is the same thing as the photosmart 1200 then you may be out of luck. Check out sane at the link above.

---

### Post by joeycbulk on 2007-03-18
I have compiled the latest version of hplip but still the same result. I am able to print but not able to use the scanner.

---

### Post by Bachstelze on 2007-03-18
run

```
sudo apt-get install sane-utils
```

If it tells you it's already installed, that's fine, then do

```
sudo sane-find-scanner
```

and paste what you get.

---

### Post by joeycbulk on 2007-03-19
I recompiled the new version of hplip. I think I made a mistake from the last time I compiled it, sorry [_PEBKAC_]("http://en.wikipedia.org/wiki/PEBKAC"). My scanner is now working... Thanks for the help! =D>  =D>  =D>

---

### Post by joeycbulk on 2007-04-04
For people who might have the same problem, check my previous posts and see if we have the same error and printer w/ scanner model.

[LIST]
[*]I reformatted my computer and encountered the error again.
[*]I compiled a new version of hplip but this time it did not solved the problem.
[/LIST] 
Tracing back the step I did before I reformat, I remembered that I unplugged then replug my printer from the usb, after that I tested xsane and the scanner worked.

I did some test to make sure that this is the only thing I need to do. 
[LIST]
[*]I reformat again and tried xsane, again my scanner did not work.
[*]I replugged it and it worked, no need to install a newer version of hplip
[/LIST]

:lolflag:

---

