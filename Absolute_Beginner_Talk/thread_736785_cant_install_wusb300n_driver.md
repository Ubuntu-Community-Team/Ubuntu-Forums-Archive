---
title: "cant install wusb300n driver"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Nuberdrive on 2008-03-27
hey, im having a heck of a time trying to install the driver for the linksys wusb300n network adapter. ive installed ndiswrapper, and i selected the .inf file needed, and installed it. but now when i open ndiswrapper, it says no drivers are installed, and when i try to re install the driver, it says its already installed. and when i plug in the adapter, nothing happens... im really new to ubuntu, so be easy

---

### Post by chucky chuckaluck on 2008-03-28
> **Nuberdrive said:**
> hey, im having a heck of a time trying to install the driver for the linksys wusb300n network adapter. ive installed ndiswrapper, and i selected the .inf file needed, and installed it. but now when i open ndiswrapper, it says no drivers are installed, and when i try to re install the driver, it says its already installed. and when i plug in the adapter, nothing happens... im really new to ubuntu, so be easy

when i was new, i found ndiswrapper really hard to figure out. however, ndisgtk made it a lot easier for me. open a terminal and do *sudo apt-get install ndisgtk* to install it and then enter *ndisgtk* in the terminal to open it (you might have to enter *sudo ndisgtk*. it's been a while).

---

### Post by Nuberdrive on 2008-04-09
aw, sweet. thank you. so you thiink this is the problem? is ndiswrapper just a faulty program?
so ndisgtk is just a seperate program i assume

---

