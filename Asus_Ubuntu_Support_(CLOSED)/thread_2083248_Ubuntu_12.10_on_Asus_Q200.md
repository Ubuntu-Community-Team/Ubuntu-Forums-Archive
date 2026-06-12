---
title: "Ubuntu 12.10 on Asus Q200"
date: 2012-11-11
forum: Asus Ubuntu Support (CLOSED)
---

### Post by nikivanov on 2012-11-11
I just bought this laptop ([http://usa.asus.com/Notebooks/Superior_Mobility/Q200/](http://usa.asus.com/Notebooks/Superior_Mobility/Q200/)), wiped win8 and installed Ubuntu 12.10 64bit. The processor is correctly recognized but Graphics is listed as Unknown.  The chipset is Intel HM76. Is there a driver I can install for Ubuntu to take advantage of the graphics adapter?

Thanks!

---

### Post by nikivanov on 2012-11-12
Fixed it by running:

sudo apt-get remove mesa-utils

reboot and run:

sudo apt-get install mesa-utils

Now it says: "Intel SanbyBridge Mobile"

I'm not sure if this helped loading the proper video driver, or if the driver was loaded this whole time and it's just the diagnostics utility that couldn't identify the video chip.

---

