---
title: "wireless issues"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by natman on 2006-05-15
Hi i have brezzy and a broadcom belkin F5d 7010 wrieless card, anyway i never got it to work even after ndiswrapper stuff.
But I read eleswhere the following
[HTML]Note: this is a defunct method written for hoary. Breezy and dapper both come with precompiled ndiswrapper modules. If those do not work try using the instructions on the ndiswrapper website. Dapper includes drivers for broadcom that do not require ndiswrapper as well.[/HTML]

Does this mean that if i install dapper, I should have no problems connecting to my wireless network?, If so is Dapper safe at the moment for a newbi to use, and when is the final release?

Thanks:
patrick

---

### Post by MasonM on 2006-05-15
Breezy comes with ndiswrapper installed, but you have to install ndiswrapper-utils in order to use it.

After installing ndiswrapper-utils, install the windows driver for you card using ndiswrapper -i <path-to-driver.inf>

Do ndiswrapper -l to ensure the driver is loaded and hardware present

ndiswrapper -m

modprobe ndiswrapper

then configure your card in System>Administration>Networking

---

