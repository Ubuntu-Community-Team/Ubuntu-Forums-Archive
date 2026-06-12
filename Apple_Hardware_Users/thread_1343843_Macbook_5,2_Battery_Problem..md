---
title: "Macbook 5,2 Battery Problem."
date: 2009-12-02
forum: Apple Hardware Users
---

### Post by Tuesdays on 2009-12-02
For some reason the only thing left that I can't get to work is the battery, the icon always appears as it plugged in, and when I go to the settings and click the only display icon when battery is present, no icon appears. Any help?

:KS

---

### Post by linuxopjemac on 2009-12-02
nr 17 in [http://ubuntuforums.org/showthread.php?t=1327758&highlight=macbook+5%2C2+battery](http://ubuntuforums.org/showthread.php?t=1327758&highlight=macbook+5%2C2+battery)

---

### Post by Tuesdays on 2009-12-02
Sorry but I am new to Ubuntu, any more help as I don't get that? lol.

---

### Post by Geremia on 2011-05-06
> **Tuesdays said:**
> For some reason the only thing left that I can't get to work is the battery, the icon always appears as it plugged in, and when I go to the settings and click the only display icon when battery is present, no icon appears. Any help?

:KSUbuntu 11.04 thinks my MacBook 2,1's battery is completely dead. Perhaps it is, but I can't tell because the button that shows the battery level on the LEDs on the battery is stuck in on my laptop... Thanks

---

### Post by Silmathoron on 2011-05-07
well, you could try ```
sudo apt-get install acpi
```
And then add acpi=force in /boot/grub/grub/cfg, as shown here [http://ubuntuforums.org/showthread.php?t=1327758&highlight=acpi](http://ubuntuforums.org/showthread.php?t=1327758&highlight=acpi) (last highlighted of the 1st post)

---

