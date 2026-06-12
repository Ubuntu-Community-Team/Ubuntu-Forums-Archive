---
title: "Adding Printer, HP psc1315 all-in-on"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by CapitanYochua on 2007-08-26
How do I add this printer please?

---

### Post by wjp.reg on 2007-08-26
> **CapitanYochua said:**
> How do I add this printer please?

what have you tried? [Open Printing Database]("http://www.linuxprinting.org/printer_list.cgi?make=HP") says it is "perfectly" compatible.

---

### Post by por100pre1 on 2007-08-26
Check in **Sistema> Preferencias** for **HPLIP Toolbox**. If it's not there, install it:

```
sudo apt-get install hplip
```

This Toolbox has everything needed to configure it.

Greetings from the Metro Area. :):)

---

### Post by CapitanYochua on 2007-08-26
I followed this liink. [http://ubuntuforums.org/showthread.php?t=47520](http://ubuntuforums.org/showthread.php?t=47520)
Still doesn't work though.   I'll try that hplip thing now.

---

### Post by CapitanYochua on 2007-08-26
I didn't find any HPLIP  thing in preferences even after running the command.

---

### Post by por100pre1 on 2007-08-26
Try this command to run it.

```
/usr/bin/hp-toolbox
```

---

### Post by jimrz on 2007-08-26
> **CapitanYochua said:**
> I didn't find any HPLIP  thing in preferences even after running the command.

- you may need to use allacarte to add to your menu
- if you are using the deskbar applet in the panel start typing hplip in it and it should offer you the choice to launch the tool box
- or ```
hp-toolbox
```

---

### Post by CapitanYochua on 2007-08-26
I got this error using the commands.
error: PyQt not installed. GUI not available. Exiting.
error: PyQt/Qt initialization error. Please check install of PyQt/Qt and try again.

Also, any reason my printer isn't working even after following the link I posted?

---

### Post by por100pre1 on 2007-08-26
It needs this:

```
sudo aptitude install python-qt3
```

---

### Post by CapitanYochua on 2007-08-26
So what do I do now to get the printer to work?

---

### Post by por100pre1 on 2007-08-26
Once in the HP Device Manager press the INSERT key (in your keyboard) and follow the instructions.

---

### Post by CapitanYochua on 2007-08-26
Well when I run the command hp-toolbox I get a message saying "no Installed Hp Devices found". I  also get some error outputs in the terminal.


HP Linux Imaging and Printing System (ver. 1.7.3)
HP Device Manager ver. 9.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

### Post by por100pre1 on 2007-08-26
Did you turned on your printer? Try checking its cables, otherwise I got no other ideas. :(

EDIT: Try running the command with sudo, just in case:

```
sudo /usr/bin/hp-toolbox
```

---

### Post by CapitanYochua on 2007-08-26
Still the same problem. I tried the command lsusb and it shows my printer; so I'm guessing the cables are fine.

---

### Post by por100pre1 on 2007-08-26
> **CapitanYochua said:**
> Still the same problem. I tried the command lsusb and it shows my printer; so I'm guessing the cables are fine.

Sorry for not being able to help you further, I'm a n00b. :(

Try using these other tools:

```
/usr/bin/system-config-printer
```

and:

```
gnome-cups-manager
```

---

