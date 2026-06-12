---
title: "help w HP LaserJet-6L (dapper)"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by stevieb on 2007-04-14
hello,

my HP LaserJet-6L will not print.  It is automatically detected and installed correctly (running dapper), and I've tried the various drivers that are available, including the recommended one.

When I try to print a test page, the job shows up in the print queue as "printing," but there is nothing happening.

this printer is listed in the ubuntu compatibles list as ok; i think i've done something wrong on this end.

any ideas?  point me in the right direction?

thanks,

-steve

---

### Post by rdd on 2007-04-14
Hi Steve, 

what kind of machine is the printer attached to. There are some problems with the parallel ports on some laptops. You could also run 'dmesg' in a terminal and post the output. That should give some clues. 

Regards

tom

---

### Post by stevieb on 2007-04-14
it's connected to an 800mHz Celeron desktop.

the dmesg command gives a lot of output; is there a certain section you're interested in, or should I post the whole thing?

thanks,

-steve

---

### Post by NewJack on 2007-04-14
Hi Steve,
  Your printer is supported by the HPLIP driver.  Go to the following link and download the HPLIP drivers:

[http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)  

Go here and make sure you have the right dependencies installed before installing the drivers:

[http://hplip.sourceforge.net/install/manual/distros/ubuntu.html](http://hplip.sourceforge.net/install/manual/distros/ubuntu.html)

Then just follow the instructions on the download page to install.

I have a LaserJet 1200 that I just recently installed using these drivers and it worked like a charm.

Good Luck!
Joe

---

### Post by stevieb on 2007-04-14
I'm trying that, but I get the following error:
```

HP Linux Imaging and Printing System (ver. 1.7.3)
Printer/Fax Setup Utility ver. 4.5

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
error: No devices found.Please make sure your printer is properly connected and powered-on.

```

What did i forget?

here's some more info- previously, dapper auto-detected the printer.  now, after hitting the above error, i tried installing the printer again through the System>Administration>Printing dialog; now this won't auto-detect the printer anymore.  don't know if that means anything...
thanks,

steve

---

### Post by NewJack on 2007-04-14
One thing that I did that I left out (sorry, just thought about it) was....

After installing the HPLIP driver, I then went into the printers option (like you are going to install the printer) and when you get to the screen that has an option "Driver", navigate to the folder where the drivers were stored and choose the driver for you printer and that should work.  It did for me anyway.  Hope that helps!

Joe

---

### Post by stevieb on 2007-04-14
thanks; i'm not sure where to look for the driver...

-steve

---

### Post by NewJack on 2007-04-14
I think mine were in  /usr/share/cups/hplip

I am not home right now and I might be wrong.

---

### Post by stevieb on 2007-04-15
i tried /usr/share/cups/model/foomatic-ppds, but got an error saying "hpijs driver already installed"

thanks,

-steve

---

### Post by stevieb on 2007-04-15
> **NewJack said:**
> One thing that I did that I left out (sorry, just thought about it) was....

After installing the HPLIP driver, ...

this seems to be where i'm stuck.  running the hplip 1.7.3 installer only gets me to the above error (badDevice).

the printer has already been added through gnome-cups-manager, but the hplip installer cannot see it.

-steve

---

### Post by stevieb on 2007-04-15
here's some more info:

when i run lpstat -s i get:
```

no system default destination
lpstat: No destinations added
```

-steve

---

### Post by stevieb on 2007-04-15
when i try to install the printer using gnome-cups-manager, at the first step it says "no printers detected,"  and under "use another printer by specifying a port," the only two options are "HP Fax (HPLIP)" and HP Printer (HPLIP)."  Is this correct?

-steve

---

### Post by stevieb on 2007-04-15
here is the contents of /etc/cups/printers.conf:
```

#Printer configuration file for CUPS v1.2.2
#Written by cupsd on 2007-04-15 10:12
```

-steve

---

### Post by stevieb on 2007-04-15
went back to hplip installation page- saw that the automatic install doesn't support parallel](*,) ; will try custom this time...

---

### Post by 11hjpphty76lkjj on 2007-04-16
After the install (custom I'm assuming at this point) make sure that ppdev is loaded.

```
lsmod | grep ppdev
```

if not:

```
modprobe ppdev
```

To have it load on boot you'll want to add it to the /etc/modules file.

Also to make sure that hplip is "seeing" the printer run:

/usr/lib/cups/backend/hp

post the output of that if you continue to experience problems.

A

---

