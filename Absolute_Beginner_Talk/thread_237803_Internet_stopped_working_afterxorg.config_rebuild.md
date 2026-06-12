---
title: "Internet stopped working afterxorg.config rebuild"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by rosdahale on 2006-08-16
Right im a newbie at this so ill make ill describe it as simple as I can. Installed Ubuntu. Installed fimrware and details and got speedtouch 330 modem working - broadband working fine !. Installed nvidia drivers, had to rebuild xserver using (sudo dpkg-reconfigure xserver-xorg) after an error screen. Boots up, everything looks nice and fresh, nvidia drivers working fine but now the internet is now working again. Redid the tutorial I did previously for 330 put still no joy, now noticed two firmware folders in firmwire, so I copied both .bin files to both but still no joy,

---

### Post by rosdahale on 2006-08-16
> 
working fine but now the internet is now working again


Sorry make that, its not working now :-?

---

### Post by powder on 2006-08-16
Xorg.conf has nothing to do with the internet, it is simply the configuration file for the X server.  Also, if you installed the nvidia driver, and then did *sudo dpkg-reconfigure xserver-xorg*, your nvidia driver is probably not working.

As far as your internet not working, you will have to give us more information (nic card, wired/wireless, etc.)

---

