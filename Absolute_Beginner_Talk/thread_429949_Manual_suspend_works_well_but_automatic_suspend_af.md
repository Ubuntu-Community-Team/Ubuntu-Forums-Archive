---
title: "Manual suspend works well but automatic suspend after inactivity doesn't..."
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-05-01
Hi,

suspend (sleep) seems to work OK when invoked by the shutdown menu or clicking on suspend in the Gnome Power Manager applet. However in Gnome Power Manager applet I set the computer to go to sleep after 5 minutes when on battery but this never happens :confused: I tried with laptop mode enabled and disbaled but it doesn't make any difference.

Any easy solution (possibly not a script but...) to have the computer go into sleep after a period of inactivity?

---

### Post by kilou on 2007-05-02
OK finally got it to work. I installed uswsusp and modified the sleep and hibernate script as follow:

/etc/acpi/sleep.sh: erase everything except #!/bin/bash and type s2ram -f
/etc/acpi/hibernate.sh: erase everything except #!/bin/bash and type s2disk

Both suspend and hibernate work fine now.....but this is a quite harsh way to do this no? Should I leave some stuff in these scripts or does s2ram and s2disk just care about everything????

---

### Post by phenest on 2007-10-13
Yes, a bit harsh, and what if you need to put back what you've deleted? Instead, put the needed s2ram line in folled by exit. Then it won't execute the rest, and you haven't deleted it either.

```
#!/bin/bash

s2ram -f

exit 0

(rest of the code stays here)
```

---

### Post by nick_h on 2007-10-13
The scripts do things like stop cron jobs, unload modules, stop services and stop the network.  They are then started again after resume.

If you have no problems with your network or anything else on resuming it is probably OK not to run the scripts provided.

You could always make sure the following settings are false in your /etc/default/acpi-support file.  This will prevent code from running that will already be provided by s2ram.

SAVE_VBE_STATE
POST_VIDEO
SAVE_VIDEO_PCI_STATE
USE_DPMS
DOUBLE_CONSOLE_SWITCH

If you want to stop the standard scripts from running then phenest's idea is a good one.

---

