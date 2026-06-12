---
title: "How do I get Fedora 7 in my Ubuntu grub list?"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by 67GTA on 2007-04-29
I want to keep Ubuntu as my primary OS. I told the Fedora installer not to reinstall grub because Fedora may or may not hang around. How to I add Fedora as a boot option in my Ubuntu grub list?

---

### Post by annda on 2007-04-29
first off, find what partition fedora is installed on.

then add an entry in /boot/grub/menu.lst under other filesystems (if you put it in the ubuntu section, it will be deleted after a kernel upgrade). as to what needs to be included there, search fedora documentation on grub setup - every distribution needs different grub options, simply copying and modifying the ubuntu entry for the right partition may not work.

---

### Post by 67GTA on 2007-04-29
Yeah, I tried the chainloader approach and had to use my super grub disk to boot back into Ubuntu. :(  I will try the Fedora documentation and see if it will help.

---

### Post by LaurelLynn on 2007-04-29
Dear 67GTA,

You can always back up the Ubuntu bootloader with the command:

$ sudo dd if=/dev/hda of=BOOTLOADER bs=446 count=1

If your harddrive is "hda" it might be somthing else: hdb, sda...

Then install fedora, write down all the entries in /boot/grub/menu.lst that it put in for itself.
Then you restore the Ubuntu bootloader with:

$ sudo dd if=BOOTLOADER of=/dev/hda bs=446 count=1

Now you can boot Ubuntu again, and add a new entry for Fedora based on what you wrote down.

Just be very sure you have the right names, size and count for everything.  dd can scramble a hard drive if you aren't careful.

---

### Post by Billy McCann on 2007-04-29
> **67GTA said:**
> I want to keep Ubuntu as my primary OS. I told the Fedora installer not to reinstall grub because Fedora may or may not hang around. How to I add Fedora as a boot option in my Ubuntu grub list?
You installed the test4 ?

---

### Post by 67GTA on 2007-04-29
I playedwith the live cd for a couple of days and decided to install it. It seemed pretty stable.

---

### Post by LaurelLynn on 2007-04-29
The easiest thing to do may be to go to a Fedora forum, and ask if someone will post their menu.lst for you. Then you should just need to change the partition names and add the entry to the end of Ubuntu's menu.lst.

---

### Post by Billy McCann on 2007-04-29
> **67GTA said:**
> I playedwith the live cd for a couple of days and decided to install it. It seemed pretty stable.

Yeah.  It seemed very stable to me too.  

what I do is just keep a Super Grub Disc handy.  I let the new distro write to the MBR and if I decide I don't want it, I bomb the partition and then slap in the Super Grub Disc which will automatically fix GRUB.  (Gnu/Linux > Advanced>Restore Grub>Automatically)

Might not be the most elite way of doing it.  Might not be the smartest.  But it's easy and it worksforme.

---

