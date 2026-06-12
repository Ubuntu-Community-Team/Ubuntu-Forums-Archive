---
title: "Powerbook Under ubuntu"
date: 2007-02-22
forum: Apple PPC Users
---

### Post by jaimesharp on 2007-02-22
my powerbook 1.5ghz model is not connecting to wireless network under ubuntu 6.06 and am wondering why as slower wired macs have network connection.is it a problem with the broadcom chipset.

---

### Post by Tipo on 2007-02-22
I'm pretty sure it's the broadcom thing.  Wireless internet has never worked with Ubuntu on a mac for me... An ethernet cable will bring it up to speed.

---

### Post by Pappa_Smurf on 2007-02-22
I posted a little howto about a day/2 ago.  In there is a link that tells you how to get your wireless working (should work in 6.06).  Basically you have to manually install the broadcom firmware which is not that hard to do.

---

### Post by kmoffat on 2007-02-25
See if this helps. it got my g4 working quickly:

[http://ubuntuforums.org/showthread.php?t=165849](http://ubuntuforums.org/showthread.php?t=165849)

Basically:

sudo apt-get install network-manager bcm43xx-fwcutter
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
sudo modprobe bcm43xx

---

