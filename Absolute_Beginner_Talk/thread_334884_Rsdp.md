---
title: "Rsdp"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by Fireware on 2007-01-09
When I boot up with Xubuntu it says: 

Starting up........

[17179569.184000] ACPI: Unable to locate RSDP

[    53.775956] hdd: No disk in hard drive 
[    57.018519] hdd: No disk in hard drive 
[    57.273465] hdd: No disk in hard drive 


then some other stuff....

what does all that mean?

---

### Post by carlosfocker on 2007-01-09
Try disabling ACPI (Advanced Configuration and Power Interface) in you bios. This should make the problem go away.

---

### Post by Fireware on 2007-01-09
Okay...thank you. :)

---

### Post by Fireware on 2007-01-09
If I don't disable it, will it be a problem?

---

### Post by carlosfocker on 2007-01-10
Does it work with it disabled?

---

### Post by Fireware on 2007-01-10
I couldn't find where to disable it in BIOS.

---

### Post by carlosfocker on 2007-01-11
First does Ubuntu Complete a boot because I wasn't clear if you are able to boot into Gnome? Is this an installed version of Ubuntu or a live CD? What motherboard are you using? Is this on a laptop?

If you are trying to boot the live CD you may want to try entering in acpi=off at boot.

If Ubuntu is already installed then check out this post about editing grub on boot.

[http://www.ubuntuforums.org/showthread.php?t=189190&page=2](http://www.ubuntuforums.org/showthread.php?t=189190&page=2)

---

### Post by Sunflower1970 on 2007-01-11
I get the same error message with Ubuntu installed, but it has not ever caused me any problems that i know of

---

