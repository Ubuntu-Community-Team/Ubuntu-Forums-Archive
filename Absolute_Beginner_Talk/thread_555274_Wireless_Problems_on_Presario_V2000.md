---
title: "Wireless Problems on Presario V2000"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by cerealtx on 2007-09-19
i tried using ndiswrapper but i keep getting error code one, im searching around the forums but am still coming up short anyone know what to do??

---

### Post by linuxwizard on 2007-09-21
I didn't post enough info. Computer or wireless make/model. Look at this see if anything might help.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by PreviousN on 2007-09-21
I played around with ndiswrapper and was getting error code 1 about last week. The fix? I was selecting an .exe file instead of the .inf file.

Commonly manufacturers will post their drivers in a self extracting .zip archive with a .exe extension. You gotta extract that and then open a terminal and type "sudo ndiswrapper" (for a root/sudoed version of the program) and then when prompted for a file/driver, use the .inf file. Any other file gives you an error.

---

### Post by nystud162 on 2007-09-22
I presume your running Feisty.

go to the terminal and enter ```
lspci | grep Broadcom\ Corporation
```

and if your output is similar to "0000:05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)" then:

[http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb]("http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb")

install, reboot, viola

The only problem i have with this is that when ever i go into "lock" mode and then come out of it, the wireless doesn't work until next reboot. Im not sure if that is directly related to that, maybe I did something else to cause that.

---

