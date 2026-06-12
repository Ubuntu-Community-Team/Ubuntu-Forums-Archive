---
title: "Asus A54C backlight issues."
date: 2012-09-22
forum: Asus Ubuntu Support (CLOSED)
---

### Post by nyamina on 2012-09-22
I've got an Asus A54C running Ubuntu 12.04, and the backlight is slightly weird - it's quite bright anyway, but after the screen fades out and goes black after a period of time, it comes back at full brightness. The same is true when entering or exiting a full-screen application - the brightness jumps to maximum. Recently, a new problem has emerged where the brightness just jumps. I put my finger on the touchpad to scroll down with Firefox, and it jumps in brightness by two notches. Other times it just jumps randomly. Weird. The function buttons to adjust brightness all work.

Anybody any ideas? Thanks in advance!

---

### Post by nyamina on 2012-09-23
Nobody has any ideas? Does anybody think that I would be better off posting this in the main section?

---

### Post by varunendra on 2012-09-24
I doubt if the brightness "jumping" issue is a result of "power  saving" option in brightness settings. Try disabling the "Dim screen to  save power" option in brightness settings.

Also, I think I read somewhere that it's a bug in versions newer than 10.04 that default brightness setting is not saved and is reset to full at reboot. The workaround is to manually putting a desired value in the corresponding file that holds this setting. Although I understand that it is not exactly your problem, if you wish to try the workaround, please check the current value :
```
cat /sys/bus/acpi/drivers/video/LNXVIDEO:01/physical_node/backlight/acpi_video0/brightness
```*(the "acpi_video0" may be other than "0" in some cases, please change it accordingly if yours is different too)*.
It should be an integer (most probably 10, which means "full" brightness). Replace it with a lower value of your preference. For example, you can change it to "2" by-
```
echo 2 | sudo tee /sys/bus/acpi/drivers/video/LNXVIDEO:01/physical_node/backlight/acpi_video0/brightness
```(again, change "0" in "acpi_video0" as and if required)
Reboot and see if the setting sticks, and even more, if it helps.

---

### Post by nyamina on 2012-09-25
> **varunendra said:**
> I doubt if the brightness "jumping" issue is a result of "power  saving" option in brightness settings. Try disabling the "Dim screen to  save power" option in brightness settings.
Disabling "dim screen to save power" totally worked, thinks =) I'll try the other technique when i get back from uni today.

---

