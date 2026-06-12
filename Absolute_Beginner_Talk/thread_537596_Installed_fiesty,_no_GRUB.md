---
title: "Installed fiesty, no GRUB"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by mitchy_g on 2007-08-29
Hello,
I just installed fiesty and the installation went well. However the machine would not boot up at all. I did format my hard drive when installing, but I cant remember if there was an option to install GRUB.

I have done a bit of searching and tried various commands with no luck. (note: I am not dual booting)

Ive attached a screenshot of my drive layout to help.

Thanks,
Mitch

[ATTACH]41960[/ATTACH]

---

### Post by Marat Galiev on 2007-08-29
what error messages you see at boot time?

---

### Post by mitchy_g on 2007-08-29
No error messages, the computer just passes through the hard drive boot process and looks for a CD to boot then boot from LAN.

I am currently using the machine by booting the CD and then selecting "Boot From First Hard Drive" in the menu.

Mitch

---

### Post by Marat Galiev on 2007-08-29
hmm,check you BIOS to boot priority:
first boot device,second boot device etc.

---

### Post by mitchy_g on 2007-08-29
Yep,
The hard drive is first to boot, then CD.

Mitch

---

### Post by ramjet_1953 on 2007-08-29
Download the [COLOR="Blue"]Super GRUB disk iso[/COLOR] and burn the iso9660 image to a CD.

Then boot from the CD and see if you can recover GRUB.

Remember to burn the image SLOWLY, no faster than 4 X.

You can get the Super GRUB Disk image from here:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Regards,
Roger :cool:

---

