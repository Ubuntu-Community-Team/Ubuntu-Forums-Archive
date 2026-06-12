---
title: "Installation Error"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by ShinodaTheory on 2007-11-29
Hello all!

I posted earlier about having problems installing Ubuntu 7.10, Well, Heres something more about the particular problem I have.

After the initial kernel loads, I get a screen that says this:

[    0.456000].. MP-BIOS bug: 8254 times not connected to IO-APIC
[    0.456000] Kernal panic - not syncing: IO-APIC + times doesn't work.

But with APIC=debug and send a report. Then try booting with the 'NOAPIC' option.

Can someone help me further? 

Thanks! :)

---

### Post by ShinodaTheory on 2007-11-29
Guess no one knows? :(

---

### Post by Pumalite on 2007-11-29
Did you try noapic?

---

### Post by ShinodaTheory on 2007-11-29
Umm, How do I go about doing that?,lol

---

### Post by Partyboi2 on 2007-11-29
You can find out how to do it from one of my other posts.
[http://ubuntuforums.org/showthread.php?t=617898](http://ubuntuforums.org/showthread.php?t=617898)

---

### Post by Pumalite on 2007-11-29
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
Some to try right off:
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317

---

