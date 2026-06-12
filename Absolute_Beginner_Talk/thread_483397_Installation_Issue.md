---
title: "Installation Issue"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Selrach on 2007-06-24
I am trying to install Ubuntu, but it stops with the following few lines.

Loading ACPI services...
Starting ACPI services...
Killed

Anyone know how I can fix this?

---

### Post by krul on 2007-06-24
perhaps you could try to disable ACPI support in your bios...looks like it don't like it.

---

### Post by Selrach on 2007-06-24
ACPI has no disable option under my BIOS, but APIC does... Tried disabling APIC but still get that error.

---

### Post by BobCFC on 2007-06-24
I have read about ACPI options you can pass to the kernel.  Worth a try.

When you get to the first menu press F6 for options and add

acpi=off

I have also heard of acpi=force


EDIT: APIC is something else

---

### Post by Selrach on 2007-06-24
Tried your suggestion, but now it just loads to a console like thing and just sits there.

---

