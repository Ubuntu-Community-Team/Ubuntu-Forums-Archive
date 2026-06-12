---
title: "Is GRUB/LILO etc absolutely necessary...?"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by John E on 2006-11-22
Is there a way to boot into Linux simply by virtue of it being on an active, primary partition?

When a BIOS first boots a PC, it looks for the boot sector on the active partition of the first available hard drive. The BIOS then loads the boot sector from that partition which, in turn, contains some code to launch an OS usually (though not necessarily) from the same partition. This is called the bootstrap process. However, a Linux partition's boot sector doesn't seem to contain any bootstrap code. If I remove grub (or don't install it) my Linux partition simply refuses to boot.

Is there any way to boot into Linux without the need for a boot manager?

---

### Post by Bachstelze on 2006-11-22
In theory, yes, I guess it's possible, just erase the MBR but I honestly can't see any reason why you would want to do such a thing...

---

### Post by mo79 on 2006-11-22
Removing GRUB would be the same as removing the Windows MBR, I think. Can be done, but not worth anything.

---

### Post by steven8 on 2006-11-22
If Ubuntu is the only OS on the computer, it just takes a couple of seconds to start grub and then loads Ubuntu.

---

### Post by John E on 2006-11-22
It's just that the MBR is where the drive's partition table is stored. Each time I install Ubuntu, something corrupts my partition table. I suspect GRUB but I'm not 100% certain.

However, if I don't install GRUB (as is possible with some other Linux distros) the Linux partition refuses to boot... :confused:

---

### Post by Bachstelze on 2006-11-22
What do you mean "corrupts my partition table" ? I don't think GRUB is the problem...

---

### Post by John E on 2006-11-22
Each time I install Ubuntu (and bear in mind I've installed ti 3 times now) Partition Magic tells me that one of my partitions has conflicting LBA and CHS values. I've been using Partition Magic for nearly 10 years and I find it very dependable.

I don't know if this is a cast-iron rule - but up until now, it's always been the 2nd Linux partition that had the problem (usually, the one I selected as the swap partition).

---

### Post by John E on 2006-11-22
I've made some progress on this one. I read on a Unix forum that Unix partitions don't make much use of CHS values so they're often left with garbage values after a re-format. Maybe the same applies to Linux?

Anyway - allowing Partition Magic to fix the discrepancy doesn't seem to have done any damage.

---

### Post by Bachstelze on 2006-11-22
I never use PM so I honestly couldn't tell you what's wrong but I have done about 50 installs of various distros on my drive and never had any problems.

---

### Post by maximouse on 2006-11-22
> **John E said:**
> When a BIOS first boots a PC, it looks for the boot sector on the active partition of the first available hard drive.

Actually, the BIOS executes the MBR, which then executes the boot sector of the active partition. GRUB or LILO is usually installed on the MBR.

> **John E said:**
> Is there any way to boot into Linux without the need for a boot manager?

No, not that I know of. But you can install LILO on the boot sector of the partition you have linux installed on, and use PM:s boot manager, or Windows boot manager to select it. This way the MBR is left intact.
You can then configure LILO to boot linux without any menu or delay.
I don't know if this is possible for GRUB as well, since I have never tried it, but I would suspect it is.

---

### Post by John E on 2006-11-22
> **maximouse said:**
> you can install LILO on the boot sector of the partition you have linux installed on, and use PM:s boot manager, or Windows boot manager to select it. This way the MBR is left intact.
That sounds more like what I need. Does LILO come with the Ubuntu live CD or if not, where can I download it?

---

### Post by turbojugend_gr on 2006-11-22
I could suggest that GRUB is definatelly not the problem. GRUB (on the contrary to LILO's default behavior) doesn't install itself on the MBR, it just creates a link to /boot/grub which it is obvious to be on your root (/) partition. If you need to be more sure of this try this [GRUB how-to/introduction]("http://www.linuxjournal.com/article/4622"), it's a bit old but it's what got me familiar with GRUB anyway.

In this how-to the first steps use a boot floppy, so you will be sure that your partition tables have nothing to do with GRUB while performing those steps, so if the problem remains the same, then it's a Partition Magic thing, I would use the Gparted LiveCD (25mbs).

Best Regards, TJ.

---

### Post by John E on 2006-11-22
Another GRUB related question - is it possible to change the default selection so that it boots into Windows by default?

---

### Post by turbojugend_gr on 2006-11-22
Yes you can, just open menu.lst "sudo gedit /bott/grub/menu.lst" and where it says "default       0" where 0 (zero) put thenumber of windows in the list starting the count from 0 not 1, so if windows is the 4rth choice (a usual case in a dual boot system) then "default    3" should do it. Make sure you have kept a copy of the file before saving.

---

### Post by maximouse on 2006-11-22
> **John E said:**
> Does LILO come with the Ubuntu live CD or if not, where can I download it?

It is included in ubuntu main. I don't know if it's on the cd, but I think it is.
A word of caution however, changing bootloaders is not a trivial task.

---

