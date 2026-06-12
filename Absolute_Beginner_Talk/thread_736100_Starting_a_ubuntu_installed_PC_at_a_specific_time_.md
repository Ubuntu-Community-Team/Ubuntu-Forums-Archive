---
title: "Starting a ubuntu installed PC at a specific time each day"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by cemlouis on 2008-03-26
I don't know this is the right place to ask this but I want to start a ubuntu installed PC at a specific time each day. How can I accomplish this?

---

### Post by kolisikepu on 2008-03-26
Walking to the PC at the time you want it on and push the "ON" button... what the???  :lolflag:

If you find out, I would like to know too.  I wouldn't mind waking up to my PC already on and ready for work.

---

### Post by glennric on 2008-03-26
This can be accomplished by creating a script with the lines
```
#!/bin/bash
echo "YYYY-MM-DD HH:MM:SS" > /proc/acpi/alarm
```
Hopefully you can figure out what I mean with YYYY-MM-DD HH:MM:SS.

This may not work.  It depends on if your bios has real time clock support or not.

---

### Post by notwen on 2008-03-26
As long as Ubuntu boots up by default in your GRUB menu, this setting would need to be set in your BIOS.  Some BIOS support system startup, but you would need to check your individual BIOS for said settings.

---EDIT---
This [thread]("http://ubuntuforums.org/showthread.php?t=727881") also wanted a PC to power up at  certain time.

---

### Post by kpkeerthi on 2008-03-26
[http://www.mythtv.org/wiki/index.php/ACPI_Wakeup](http://www.mythtv.org/wiki/index.php/ACPI_Wakeup)

---

### Post by glennric on 2008-03-26
I forgot to point out, that you would then need to make the script executable and run it with sudo.

---

