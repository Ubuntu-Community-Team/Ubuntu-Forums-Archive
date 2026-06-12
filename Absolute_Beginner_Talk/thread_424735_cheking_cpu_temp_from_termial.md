---
title: "cheking cpu temp from termial?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by kfehr911 on 2007-04-27
My fan was running for a long time today and was wondering if I could check the temp with out having to go to bios.  Any pointers or reading out there for me?

---

### Post by Novastorm on 2007-04-27
With my HP nx9040 running 7.04 I can check the temperate by simply typing in a terminal

```
cat /proc/acpi/thermal_zone/THRM/temperature
```

Yours may not be that exact same path, but try looking around in that similar location.

You could also look at installing the GNOME sensors applet.

```
sudo apt-get install sensors-applet
```

---

### Post by stmiller on 2007-04-27
Yeah sudo apt-get install sensors

Then just type 'sensors' in a terminal.

---

### Post by kfehr911 on 2007-04-28
I can't say that worked for me. I would like to use the applet version. I'm a GUI user and not great with terminal.  Does 6.10 have that same feature?

---

### Post by Najand on 2007-04-28
Do you have the themral sensor hardware? If not htere won't be anything for you to see.

---

### Post by DarkN00b on 2007-04-28
Try

```
acpi -V
```

That's a capital V.

---

### Post by kittyhawk63 on 2007-04-28
How do you reverse the following install? I want to uninstall it.

sudo apt-get install sensors

kh

---

### Post by DarkN00b on 2007-04-28
To uninstall this package:

```
sudo apt-get remove sensors
```

---

### Post by kittyhawk63 on 2007-04-28
> **DarkN00b said:**
> To uninstall this package:

```
sudo apt-get remove sensors
```

Thanks.
kh

---

### Post by Roger Mudd on 2007-04-28
If you're a GUI guy you might want to check out lm-sensors and sensors-applet. This will give you access to your vitals (providing it is supported by your motherboard) from the desktop.
From the command line (Terminal):

```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install lm-sensors sensors-applet
```

Then right click on a blank space in the panel at the top of your screen (or wherever you want the sensors to appear) and add the "Hardware Sensor" applet that was installed in the step above. Once it appears, right click on the applet and select "Preferences." You can adjust what is displayed and how it is displayed here.
I have been lucky enough to have lm-sensors work out of the box for me on my workstation and laptop (Thinkpad T42). I have seen past threads on this board that suggest lengthy configuration processes, however. Your mileage may vary.

Hope this helps!

---

