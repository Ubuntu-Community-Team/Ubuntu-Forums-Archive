---
title: "Problem with hplip toolbox"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by Roger D on 2007-12-23
Hi

I've an hp 3650 printer, and I'm running Dapper. I'd like to know how much ink I've got left. It appears the hplip toolbox can tell me this, but I can't get it to work.

I've manged to get the toolbox icon to to appear under System>Administration, but when I clip on  the icon, I  get a message from the HP Device Manager telling me I've 'no installed HP Devices'. Which is odd, as I selected the printer during installation, and it seems to work fine.

Any ideas, anyone?

Best regards

Roger D

---

### Post by linuxwizard on 2007-12-23
For HP Toolbox to work have you installed 3 packages for it ?  python-qt3, python 2.4-qt3,  python2.4-sip4-qt3 > search for these make sure installed.

---

### Post by Roger D on 2007-12-23
Yes, just checked, all installed

---

### Post by linuxwizard on 2007-12-23
Open Toolbox > Device tab > Setup New Device > than add your printer

---

### Post by Roger D on 2007-12-24
Can't do that. When I open the toolbox, I get two windows: in the background there's a window HP Device Manager (which doesn't have a 'devices' tab); in the foreground there's a window headed 'HP Device Manager - No Installed HP Devices'

---

### Post by linuxwizard on 2007-12-24
Not sure what you have going on should not have 2 windows. HP Toolbox =HP Device Manager. Try this in terminal > hp-toolbox  > see if you get 1 window. You have to add that printer into the Toolbox.

---

### Post by Roger D on 2007-12-25
Here's what I get in my terminal.


 roger@roger-desktop:~$ hp-toolbox

 HP Linux Imaging and Printing System (ver. 0.9.7)
 HP Device Manager ver. 6.0

 Copyright (c) 2003-5 Hewlett-Packard Development Company, LP
 This software comes with ABSOLUTELY NO WARRANTY.
 This is free software, and you are welcome to distribute it
 under certain conditions. See COPYING file for more details.

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

I then get the two windows with the message: 'No installed HP device found', which I find strange, as I've perfectly functioning HP 3650 printer, apart from being able to access 'services and status' via the toolbox. It's as though toolbox doesen't recognise my printer drvier.

Be nice to get to the bottom of this. I want to buy an HP printer/scanner/copier, but I need to know the toolbox actually works.



Merry Christmas

Roger D

---

### Post by Sef on 2007-12-25
I don't think I could get it working in Dapper.  However, you might try updating the [HP Toolbox]("http://hplip.sourceforge.net/supported_devices/index.html").

---

### Post by Roger D on 2007-12-26
Not much success at updating the hplip toolbox either.

I did a download, storing hplip-2.7.12(2).run on my desktop. Then followed the installation instructions on the HPlip website. The suggested terminal command hplip-2.7.12.run failed; so I tried hplip-2.7.12(2).run, which didn't work either.

roger@roger-desktop:~$ sh hplip-2.7.12.run
sh: hplip-2.7.12.run: No such file or directory
roger@roger-desktop:~$ sh hplip-2.7.12(2).run
bash: syntax error near unexpected token `('
roger@roger-desktop:~$

Anymore ideas, anyone?

Roger D

---

### Post by rleonard on 2007-12-27
I didn't have any luck using the run file, I had to use the tar file and update the packages by hand, the script in the installer didn't work for me (showed what packages were required but couldn't get them).

---

