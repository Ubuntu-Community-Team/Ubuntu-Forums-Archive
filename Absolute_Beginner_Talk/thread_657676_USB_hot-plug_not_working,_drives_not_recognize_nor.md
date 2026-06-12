---
title: "USB hot-plug not working, drives not recognize nor mounted"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by franfran on 2008-01-03
hey guys,

when i plug in my USB drive, my hdd, cell phone or camera, none of them show up or show that its mounted.

its not even recognized that its plugged in when i look at the "my computer". but when i reboot my computer, it mounts and recognizes all those drives properly like its not a problem.


someone told me to check the hot-plug and enable it on my bios, but there is no such settings. i have a hp pavilion dv6000 laptop.



any thoughts?

---

### Post by spiderbatdad on 2008-01-03
as far as i know, hotplugging of certain devices, in particular the ones you mentioned, is still unresolved. You can of course mount the devices from the terminal, or write a simple bash script (simple if you know how) to do it for you when you run a command.

---

### Post by jcaveman on 2008-01-05
If you added the noapic option in order to boot, then the usb ports got disabled.  Try adding irqfixup to the boot options.

---

### Post by freddyp on 2008-01-05
Not to insult, but have you checked:

System>Preferences>Storage Tab and made sure the following items are checked:

Mount removable drives when hot-plugged
Mount removable media when inserted
Browse removable media when inserted

Don't ask me how I know how easy it is to accidentally uncheck one :redface:

---

