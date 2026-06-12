---
title: "It won't install"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by jeffrey45323 on 2007-09-26
When I try to install my xubuntu, it just comes up with an error message that says unable to locate RSDP and then goes to a command prompt screen that informs me [    29 .775854 ]    <0> Kernel panic - not syncing: Attempted to Kill the idle task!
[   29.776042 ]

---

### Post by reckless2k2 on 2007-09-26
are you using the alternate cd or the livecd?

give us some details about the pc as well.

---

### Post by jeffrey45323 on 2007-09-26
7.04 "Fiesty Fawn" i386 on a Toshiba Satellite pro 445 CDT

---

### Post by reckless2k2 on 2007-09-26
if you are using the livecd try the alternate cd instead. might help.

---

### Post by Linux_Man on 2007-09-26
Try either reburning the live-cd or install disc at a lower speed setting if possible, check the integrity of your CD and if those don't work try redownloading the ISO. It could be your computer but sometimes those errors are a result of a scratched disc or a improperly burned CD

---

### Post by ddrichardson on 2007-09-26
RDSP is part of the ACPI system, try booting with the acpi=off option appended to the kernel line (F6)

---

