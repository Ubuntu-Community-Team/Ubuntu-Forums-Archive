---
title: "Usb Flash Drive Problem"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by Tangerined on 2006-09-27
I have a problem mounting my usb drive. It was working before I rebooted but after I rebooted it would not mount. The message it gave me is "Unable to mount selected volume, Mount: only root can mount /dev/sdc1 on media/sdc1" The weird thing is that if I stick 2 drives in, the first one would not mount but the 2nd one will. If i reverse the order I get the same thing so its not my usb drives problem.

---

### Post by nts on 2006-09-27
if it is asking to be root, then you need to be root - in order to do this in a grpahical way try:

gksudo nautilus

---

### Post by Tangerined on 2006-09-27
Ok cool thanks that worked, but is there a way to not have to be root? because now every time i want to mount it or eject it, I have to be root. I mean before the reboot I didn't have to be root to do this stuff.

---

