---
title: "Wi-Fi don't work"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by Landrovan on 2007-10-16
Hi,

I just build my new PC. I installed kubuntu Gusty 32bit (the RC). Here the spec:

Motherboard: Asus P5K-E Wifi/AP edition
Proc: Intel Core2 Quad 2.4GHz
Video card: GeForce 8500 GT

The installation went well and kubuntu work, but the wifi doesn't work (i haven't tried the ethernet wired). So I download the driver for linux on the Asus site. There is only one package for linux that contain 4 drivers (lan, wifi, raid and audio). But I can't compile the wifi drivers (haven't tried the 3 others). I have an error saying that INIT_WORK that 2 argument and not 3. On other forum I found that the 3 parameters version are not in kernel upper than 2.6.19.

What can I do?

---

### Post by bsharp on 2007-10-16
Make sure you have the build-essential package installed

---

### Post by Pumalite on 2007-10-16
Wireless:

[http://www.linux.com/feature/56946](http://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

---

### Post by magicfab on 2007-10-16
This may sound obvious, but does does your chipset require restricted drivers ? Maybe they're just not active by default. Look into System > Administration > Restricted Drivers manager.

---

