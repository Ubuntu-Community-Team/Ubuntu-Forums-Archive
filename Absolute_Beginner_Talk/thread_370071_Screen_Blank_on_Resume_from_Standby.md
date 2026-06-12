---
title: "Screen Blank on Resume from Standby"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by zobojoe on 2007-02-25
I'm new to Ubuntu - first impressions are very :) 

However on resume from Standby, the screen on monitor remains black - the box sounds like it is resuming properly but LED on monitor remains at Amber  - only way out is to reboot !!

I've tried toggling the following in /etc/default/acpi-support with no luck...

```
# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true
# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true
# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true
```

It is a pretty standard Ubuntu build (No Beryl etc) and I have a NVIDIA 7900 GTX card with correct drivers installed.

---

### Post by n8bounds on 2007-02-25
Not sure.  Did a quick search and found these, maybe you haven't already read them...

[http://ubuntuforums.org/showthread.php?t=284994](http://ubuntuforums.org/showthread.php?t=284994)

[https://wiki.ubuntu.com/LaptopTestingTeam/](https://wiki.ubuntu.com/LaptopTestingTeam/)

[http://www.columbia.edu/~ariel/acpi/acpi_howto.txt](http://www.columbia.edu/~ariel/acpi/acpi_howto.txt)

---

### Post by zobojoe on 2007-03-05
Thanks - good articles however I'm still struggling with this - in the meantime to see if I like Ubuntu I've loaded onto a hp nc6000 laptop - everything works great after sorting the printer drivers and the wifi -Linux is so cool !

Wish I could sort out the resume on my PC - anybody got any other ideas on resolving resume problems from standby ???

---

