---
title: "Imac Mid 2007 (7,1) no suspend or brightness control"
date: 2017-11-22
forum: Apple Hardware Users
---

### Post by ratell on 2017-11-22
I am running Ubuntu 17.10 LVM 64 bit as a single EFI boot on my mid 2007 Imac. 
In general Ubuntu runs great on this set up. The only roadblock has been that I need to use nomodeset as a kernel option to boot.
I also am unable to resume from suspend (suspending works fine the screen just never wakes up again).
There's also no controlling the backlight or brightness.

I'm using the open source radeon driver and set up a swap file twice my RAM (8gb).
Near as I can tell the issue is that my machine has 32bit EFI and with apple's implementation the graphics card bios doesn't fully get loaded. I could run the 32 bit version of Ubuntu and use legacy bios and suspend would work.

My questions is A. is that true? and B. Is there a way to get the resume working if I'm booting with Grub 2 and EFI on this machine?

Thanks for any advice or assistance.

Rob

---

### Post by kevin160 on 2017-11-29
I struggled for a while trying to get my macpro1,1 to suspend/wake properly.  I ended up going back to ElCap since that seemed simpler, in addition to wanting to run come OpenCL apps that wouldn't run under Linux on my old ATI 5770 card.  

Apparently it is possible on these old machines, but you need to play with the various ACPI settings to properly sleep and wake various components, and you may need to build custom DSDT definitions.  

If you make some progress, please do post about it.

---

