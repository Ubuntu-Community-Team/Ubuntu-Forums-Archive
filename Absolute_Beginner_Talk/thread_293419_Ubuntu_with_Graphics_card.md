---
title: "Ubuntu with Graphics card"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by PPAAUULL on 2006-11-05
Ok so here is what is going on. I just bought and installed a new ATI graphics card. I staerted Ubuntu up and as I thought, Xorg complained so I did a ```
sudo-reconfigure -phigh xserver-xorg
``` and now I can start up and log in the only problem is that the screen is messed up... lol. Is there anyway of fixing it or do I have to do I reinstall?

PS I already tried to start up the live cd aswell and I get xorg problems.

Thanks for the help.

---

### Post by MasterOfDisaster on 2006-11-05
Try installing the fglrx driver for your card.  Not sure if this will work, but worth a try.

[http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910)

There's a howto for it.

---

### Post by haxer on 2006-11-05
Which card do you got? nvidia/ati which model? might not be supported :S install drivers :)

---

### Post by taurus on 2006-11-05
> **haxer said:**
> Which card do you got? nvidia/ati which model? might not be supported :S install drivers :)
It says ATI graphics card on the first line!

---

### Post by PPAAUULL on 2006-11-05
ATI Radeion 9250. I am pretty sure that is what it is but my spelling might be off.

---

### Post by PPAAUULL on 2006-11-05
Ok Everytime I try to run the graphics driver install I ge theis messege ```
paulvolk@paulvolk-desktop:~/Desktop$ ./ati-driver-installer-8.27.10-x86.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.27.10......................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 156: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

```

Is there anyway to fix it or does anyone know what is going on?

---

