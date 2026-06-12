---
title: "Powerbook G4 Live boot of Ubuntu MATE 16.04.1LTS Hangs Welcome Screen Freezes cursor."
date: 2016-09-19
forum: Apple Hardware Users
---

### Post by bcharusa on 2016-09-19
Powerbook G4 Live boot of Ubuntu MATE 16.04.1LTS Hangs on "Welcome Screen" Freezes cursor, keeps me from moving forward on install. Any Ideas On how to prevent Welcome screen from launching?

---

### Post by ernsteiswuerfel on 2016-09-22
Is it a total system freeze, and you need a hard reboot (powerbutton)? If so, this could be bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1571416](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1571416). I had this problem with PowerBook G4 5,4 and  PowerBook G4 5,6 too. In my case it was enough to add following boot-parameter: radeon.agpmode=-1

If you boot the live cd you can enter it at the boot prompt like this: live radeon.agpmode=-1

After the successful installation don't forget it to your boot parameters in **/etc/yaboot.conf** inside the append="..." line. After that write the yaboot.conf to disk with **sudo ybin -v.**

---

