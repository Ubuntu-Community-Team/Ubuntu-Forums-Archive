---
title: "Setting up a web connection."
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by Network Nurd on 2006-06-16
Ok - I"ve just instaled Drake and now i'm ready to connect to the internet.  I am using a Zyxel G-200 wireless USB adapter.  In the Device manager I see the USB2.0 WLAN button.  It knows that the adapter is Zyxel - how do I configure my network to use this?  (Its not showing up in the Network Settings Window.)

Thanks!

---

### Post by az on 2006-06-16
It may be a chipset with no native linux support (the 1211 chipset works, but not the 1211b)

Maybe try first with ndiswrapper?  If that fails, you could try to look around for up-to-the-minute linux drivers from Zydas (if that is the correct manufacturer (you cannot always be sure of the exact chipset)- they are working on the linux driver for their chipset (including the revision b) currently)

---

### Post by Network Nurd on 2006-06-16
I've just installed ndiswrapper and am trying to install the driver.  Its giving me a line 135 error.  What is the default path for the folder to install the driver into?

---

