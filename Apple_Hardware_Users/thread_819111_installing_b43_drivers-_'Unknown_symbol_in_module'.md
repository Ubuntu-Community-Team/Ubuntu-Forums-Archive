---
title: "installing b43 drivers- 'Unknown symbol in module'?"
date: 2008-06-05
forum: Apple Hardware Users
---

### Post by spazo on 2008-06-05
First off i would like to give a hats off the the ubuntu development team for creating a nice (easy to use) and smooth operating linux distro for the PPC platform!

My problem is with installing drivers for the Broadcom 4306 (I think it is) chipset found in the Airport Extreme. I have an Apple iBook G4 that is a dual boot with OSX and Ubuntu Dapper. I've had the card working with the bcm43xx drivers on the linux kernel build 2.6.15 but I couldnt get the card to inject packets. So after some research I found that the newer b43 drivers supported the function but i needed to upgrade the kernel. I totaly reinstalled ubuntu all together(So I knew I couldnt screw up) then I installed kernel 2.6.25.4 and then copied the new drivers using fwcutter and installed compat-wireless. 

Now when I go to load the driver "sudo make load" I get 

"FATAL: Error inserting b43 (/lib/modules/2.6.25.4-wafflemann/updates/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)
b43 loaded successfully
b43legacy loaded successfully"

iwconfig doesnt show the card and when a run dmesg I get

"[  751.707624] b43: Unknown symbol __led_classdev_unregister
[  751.709203] b43: Unknown symbol led_classdev_register
[  751.807224] Broadcom 43xx-legacy driver loaded [ Features: PID, Firmware-ID: FW10 ]
[  752.058489] b43: Unknown symbol __led_classdev_unregister
[  752.060083] b43: Unknown symbol led_classdev_register"

Now I cant run the old bcm43xx drivers and Ive totaly redone the system two times! Is there anything I havent read clearly or is there a better driver that works out there without me redoing my system.(kinda sick of that now)

---

### Post by Joker5bb on 2008-06-16
[http://tinyshell.be/aircrackng/forum/index.php?topic=3597.0](http://tinyshell.be/aircrackng/forum/index.php?topic=3597.0)
its a complete how-to on aircracking with b43 (Broadcom) 

:lolflag:

---

