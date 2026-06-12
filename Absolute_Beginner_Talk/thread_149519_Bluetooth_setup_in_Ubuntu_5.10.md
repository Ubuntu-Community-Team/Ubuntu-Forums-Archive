---
title: "Bluetooth setup in Ubuntu 5.10"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by sscoop on 2006-03-24
i have a toshiba bluetooth device built in my tecra m2 laptop
i have noticed that in linux some bluetooth services start and also that bluez software is installed.
what i wish to know is how can i connect devices to my laptop. is there a GUI or some terminal commands? i have a nokia headset that worked fine in windows, and i want to connect that.

---

### Post by Marshall2day on 2006-03-24
Bluez is only the bluetooth demon. You'll need to install the bluetooth tools. I'm not sure what's the name of the package nut if you search the repository on bluetooth they'll pop up. It's best to install the KDE version since they have more functionality then the GNOME version.

---

### Post by jsgotangco on 2006-03-26
The Toshiba BT Module doesn't work in Ubuntu in general. I also have a Tecra M2 which is an official Canonical test unit and BT doesn't work at all. You can try the *hcitool* command to check: *sudo hcitool dev*.

I just discovered that BT in the Tecra M2 wasn't working at all (I never really checked) when I was trying to come up with a test plan for bluetooth enabled computers. I tested an old broadcom-based BT dongle and it just worked.

---

