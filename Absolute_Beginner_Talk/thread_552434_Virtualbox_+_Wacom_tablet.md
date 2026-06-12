---
title: "Virtualbox + Wacom tablet"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by onero on 2007-09-16
I'm running Virtualbox 1.5.0 on an Ubuntu Feisty host, with a WinXP guest. I can get USB devices such as my printer and flashdrives to work with the WinXP Guest; the printer even uses the Windows drivers to print (yay, because it doesn't have native linux drivers).

However, I can't get my Wacom Intuos 3 tablet to work in the same way; whenever I try to give the guest control, I get an error that a proxy couldn't be created for the USB device.

Reading up on USB devices in the VBox manual, I found out that if a driver has already claimed the device, then the proxy error will occur. Obviously, the wacom driver is being used for my tablet, so I assume this is why it can't be used in the guest ^^

Anyway, my question is, is there an easy way for me to disable the wacom driver in Ubuntu so that the tablet can be used in the WinXP guest? I really miss the pressure sensitivity and whatnot in Windows. Consequently, there also needs to be an easy way to re-enable it in Ubuntu.

I don't want to mess around with the driver too much because I might FUBAR it and have my tablet not work at all ^^ Any suggestions? Any help at all would be appreciated.

---

### Post by jessika-kaos on 2008-02-17
Bump. I'm having the same issue. Any ideas?

---

