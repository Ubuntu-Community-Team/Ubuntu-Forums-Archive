---
title: "No Mouse or Keyboard at Login"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by dr_dirk on 2007-04-04
I have been fiddling a little bit trying to get things to work.  I just rebooted and at the login screen I didn't have a mouse or keyboard available to me  Naturally I screamed and after about 30 seconds the mouse turned on and I was able to use the keyboard.  I don't know what might have caused this, but here is what I have changed recently.

I installed a printer that had been giving me a lot of trouble and required to change cupsd.conf etc.  I also was in the process of trying to set up said printer as a network share.

The other recent change I made was to uninstall the 2.6.17-10-generic kernel so that it didn't show up as a boot option in GRUB.  I'm guessing this is the most likely culprit.  If anyone has any thoughts on this, please let me know.  No mouse and keyboard at startup is nerve wracking, to say the least.  Thanks

Derek

---

### Post by dr_dirk on 2007-04-04
I tried booting in safe mode and saw an error that caught my attention.  I hope this helps someone to understand what might be wrong.

[17179610.040000] usb 7-4: device descriptor read/64, error-110
[17179613.376000] usb 7-4: device descriptor read/64, error-110
[17179628.592000] usb 7-4: device descriptor read/64, error-110
[17179633.832000] usb 7-4: device descriptor read/8, error-110
[17179638.952000] usb 7-4: device descriptor read/8, error-110
[17179644.196000] usb 7-4: device descriptor read/8, error-110
[17179649.320000] usb 7-4: device descriptor read/8, error-110

Maybe this doesn't have anything to do with the problem but I figured I may as well post it in case it does.

---

### Post by dr_dirk on 2007-04-04
bump

---

### Post by dr_dirk on 2007-04-25
The problem went away by itself at one point when I installed Beryl, for some reason.  It cropped up again when I edited the grub config file to remove kernel boot options when I boot.  I also uninstalled the unwanted kernels with synaptic.  One of those things or the combination seems to have triggered it.  I still don't know why that would happen, but that seems to be the source of the problem.

---

