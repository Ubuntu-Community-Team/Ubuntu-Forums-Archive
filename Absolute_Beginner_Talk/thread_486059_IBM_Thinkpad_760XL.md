---
title: "IBM Thinkpad 760XL"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by KeithSloan on 2007-06-27
I have a very old laptop IBM Thinkpad 760 XL that I would like to try out with Ubuntu.

Questions
1) How do I try Ubuntu? I don't think the Laptop will boot from CD :-(

2)The reason I run Windows 98 on the machine is that IBM never wrote any drivers for the PCMCIA host past Windows 98. Will the same restriction apply to Ubuntu.

Any other advice.

Thanks Keith ( awaiting Ubuntu CD in the post )

---

### Post by Phixion on 2007-06-27
You need to change boot sequence in your BIOS to boot from CD, change it to boot the CD Drive first, then it should boot from CD on reboot.

As for the second question, who knows, Ubuntu supports alot of hardware though.

---

### Post by KeithSloan on 2007-06-27
But that's the point I don't think it has a BIOS option to boot from CD :-(

---

### Post by Inxsible on 2007-06-27
How about you update the BIOS itself. You would have to get one that supports that hardware, but I am sure it wouldnt be very difficult to get a BIOS that supports booting from a CD

---

### Post by ugm6hr on 2007-06-27
> **KeithSloan said:**
> But that's the point I don't think it has a BIOS option to boot from CD :-(

This might be helpful:
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

Otherwise I know DamnSmallLinux definitely has a floppy installer.

---

### Post by KeithSloan on 2007-06-27
"How about you update the BIOS itself"

Not much chance I already have the latest BIOS and IBM do not update the BIOS after a couple of years.

Thanks for the info on SmartBoot that fix the problem.

I managed to run the LiveCD for 5.10 but in the end the X-server failed with a message. I will wait for latest version of Ubuntu to arrive and try again

---

### Post by KeithSloan on 2007-07-02
OKay after trying 5.10 I now have a copy of 7.04 fiesty fawn.

I tried to boot this via the smartboot floppy. Initially I get an error ACPI unable to locate RSDP following other stuff in forum I altered the startup options to include acpi=off and that got ride of the error msg, but now the system just goes back and accesses the floppy drive. Is there a startup option to tell it to use the CD

---

