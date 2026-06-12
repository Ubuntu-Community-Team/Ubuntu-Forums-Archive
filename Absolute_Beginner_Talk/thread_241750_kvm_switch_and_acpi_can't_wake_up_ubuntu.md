---
title: "kvm switch and acpi: can't wake up ubuntu"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by imputerate on 2006-08-22
i'm using a kvm switch [with usb connectors] to connect an ubuntu box [5.10] and a slackware box to a monitor and a pair of keyboard/mouse combinations;

root@<ubuntu box>:/etc/acpi/events # cat /proc/acpi/info
version:                 20050729

when the ubuntu box goes to sleep, it doesn't supply the power necessary for the kvm switch to relay a wake-up call from either keyboard [this is not true of the slackware box; acpi version 1.0.4];

the kvm switch mfgr [IOGEAR] says i have to keep the ubuntu system from dozing off to the point where it can't supply juice to the switch;

how do i do that?

i've been reading up on acpi, and the "config" language but:
root@UBU:~ # less /proc/acpi/event
/proc/acpi/event: Device or resource busy

[email]imputerate@puteracy.net[/email]

---

