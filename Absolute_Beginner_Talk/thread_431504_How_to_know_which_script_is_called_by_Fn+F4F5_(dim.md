---
title: "How to know which script is called by Fn+F4/F5 (dim brightness)???"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-05-03
Hi,

when I press Fn+F4 the screen brightness of my laptop increases and when pressing Fn+F5 it decreases (MSI S260). This work perfectly manually but it doesn't work automatically when going on or off the battery because Gnome power management doesn't seem to recognize my laptop. Anyway I want to do a script that will call these commands when switching on/off battery so that I can adjust the screen brightness accordingly and automatically. However for this I need to know which script is called when I press Fn+F4 and Fn+F5. Is there anyway to know that for my particular laptop???

---

### Post by dergringo on 2007-05-03
Hi

Mostly the brightness buttons are a hardware thing so no script is called. And that could be the reason why gnome power manager isn't able to decrease brightness.

greets

Philipp

---

### Post by kilou on 2007-05-03
Maybe the keys are a hardware thing but there is for sure a script related to brightness because when I switch on battery the screen dims by 2-3 notches only so something is happening. It's just that I don't know how to configure it. I've changed ac-brightness and battery_brightness in gconf under apps/gnome-power-management but it doesn't have any effect. I know there exist scripts such as panabright.sh or sonybright.sh in /etc/acpi/ but they seem to be specific to Panasonic and Sony laptops. However mine for sure reacts when I unplug the AC cord so it's probably because of a script somewhere no?

---

### Post by richjoyce on 2007-05-03
It can be the bios that changes the screen brightness...

---

### Post by Bachstelze on 2007-05-03
This is certainly done using sysfs helper files. Look around in /sys and see if you have something regarding LCD bightness.

---

### Post by kilou on 2007-05-03
Well my problem is solved thanks to msi-laptop module. Ref: [http://ubuntuforums.org/showthread.php?t=431622](http://ubuntuforums.org/showthread.php?t=431622)

Thanks!

---

