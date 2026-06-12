---
title: "Running Ubuntu from USB drive *ISSUES*"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by kevmck1 on 2008-03-29
I'm brand new to linux. 

I installed ubuntu on a usb drive using the live CD on a windows machine.

When I tried to boot from the usb after changing the boot sequence to start with usb, it would not boot.

When I changed the boot sequence back to the HDD it would not boot. I guess the install damaged the master boot record. 

I'm afraid to try the usb drive on another computer. Could it possibly corrupt the MBR on another system or was it just the install process that corrupted the MBR?

Thanks

---

### Post by wolfen69 on 2008-03-29
your usb install is not an executable file. it cant change anything on a computer. i would try changing bios settings back to default and go from there.

---

### Post by gn2 on 2008-03-29
Have a look at [www.pendrivelinux.com](www.pendrivelinux.com) for lots of useful info and how-tos

---

### Post by kevmck1 on 2008-03-29
It was my work laptop, so I sent it back to them to fix.

Do you know of any reason why it would not boot from the usb drive?

---

### Post by gn2 on 2008-03-29
Yes, there are different types of boot from USB BIOS options and not all will work booting all Linux distros from a Flash drive.

Here's a way to check: [http://www.pendrivelinux.com/2007/09/17/testing-your-system-for-usb-boot-compatibility/](http://www.pendrivelinux.com/2007/09/17/testing-your-system-for-usb-boot-compatibility/)

---

