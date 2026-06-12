---
title: "USB Drive not Showing Up"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by hsadan on 2007-07-18
The first time I plugged in my USB Drive, it worked fine, got auto-mounted and everything. Then I clicked to close the pop-up in the bottom right that told me about ejecting it to avoid damage, but when I did that the USB Drive disappeared, and even after rebooting it doesn't show up anywhere.

I've even tried doing 'sudo fdisk -l' , but it's not showing up there either (I don't see any /dev/sda/media, only /dev/hdc... ) similarly, I can't seem to find anything by doing lsusb.

The usb drive itself isn't the problem, I've put it in my winXP machine and it works fine. It's also a FAT format drive, so no problem there.

Any idea how I can get it to work?

---

### Post by FleetAdmiral74 on 2007-07-18
So after you dismounted, you verified it worked on another comp...maybe try another USB port, preferably on a different board (back of your comp or your front access)

---

### Post by skymera on 2007-07-18
i have tyhat problem sometimes.

i plug it in and dosent show
but then other times, it does.

weird, and dont know why

---

### Post by hsadan on 2007-07-18
fleetadmiral: i've eliminated the possibility that my usb port is faulty, because I tried plugging in my mouse into the same port and it worked.

skymera: wow, you are right. now it works :P.

---

