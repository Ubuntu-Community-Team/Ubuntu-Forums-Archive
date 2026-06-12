---
title: "HP LaserJet-6L not detected"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by stevieb on 2007-04-14
hello,

i've been trying to install this printer all day with hplip1.7.3 installer, but my printer is not recognized.

here's the output of /usr/lib/cups/backend/hp:

```
direct hp "Unknown"  "HP Printer (HPLIP)"
```

any help is appreciated; thanks!

-steve

---

### Post by 67GTA on 2007-04-14
HPLIP is the driver for the printer. It works with CUPS. You will have to set it up with  CUPS before you install the driver. Go to SYSTEM>ADMINISTRATION>PRINTING and it should show your printer. Configure it from there and then install the HPLIP driver. After it is installed you may have to run "sudo hp-setup" in a terminal to complete the setup. You can also go to the CUPS website and further configure the printer if the HP Toolbox in SYSTEM>PREFERENCES> does not give you the extra options.

---

### Post by ramjet_1953 on 2007-04-15
Which version of Ubuntu are you running?

If it is Feisty, I have noticed that when HPLIP is installed, it doesn't install the QT3 libraries, which are required.

If you are running Feisty, open a terminal and type in [COLOR="Red"]hp-toolbox[/COLOR]

If the terminal comes back and mentions that the QT3 libraries are missing, you will need to install them, using Synaptic.

Regards,
Roger :cool:

---

### Post by stevieb on 2007-04-15
i'm running dapper, and have installed the printer using cups, but it says "parallel port busy, will try again in 30 seconds", and nothing happens.

when i run sudo hp-setup, i get this:

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

---

### Post by earthforce_1 on 2007-12-29
Forgot to mention: reported as Bug #178822 in Launchpad
[https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/178822](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/178822)

---

