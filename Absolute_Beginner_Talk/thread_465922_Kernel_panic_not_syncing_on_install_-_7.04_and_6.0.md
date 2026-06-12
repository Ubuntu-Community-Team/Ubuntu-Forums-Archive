---
title: "Kernel panic not syncing on install - 7.04 and 6.06"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by ObscureReferenceMan on 2007-06-06
I tried installing ubuntu 6.06 and 7.04 on my old Dell, but couldn't. It kept hanging up at various points. [As it turned out]("http://ubuntuforums.org/showthread.php?t=439611"), I did not have enough RAM. So I added a 512MB chip (for a total of 640MB) and tried again.

This time, put in the 7.04 boot CD. After selecting "Install", things seemed OK. Got "Loading Linux Kernel". But then got a list of codes that started with:
[FONT="Courier New"]
[COLOR="Navy"][   75.803122]  [<c01badf0>] ramfs_get_inode+0x70/0x110[/COLOR][/FONT]

The last few were:
[FONT="Courier New"][COLOR="Navy"][  75.804554]  [<c03d77ea>] start_kernel +0x35a/0x420
[  75.804646]  [<c03d7230>] unknown_bootoption
[  75.804790]  ===============
[  75.804790] Code: 42 04 89 4a 08 a9 00 00 10 00 75 23 a9 00 00 20 00 74 9b 0f 0b eb fe 8b 4c 24 04 89 41 08 e9 2e ff ff ff 0f 0b eb fe 0f 0b eb fe <0f> 0b eb fe 0f 0b eb fe eb 0d 90 90 90 90 90 90 90 90 90 90 90 
[  75.807045]  EIP : [<c01ef2e9>] radix_tree_insert+0x1c9/0x1e0 ss:esp 0068:c03d371c
[  75.807185]  <0>Kernel panic - not syncing: Attempted to kill the idle task!
[  75.807280][/COLOR][/FONT]

At this point, everything stopped. Could not do anything - Enter, F1-F12, etc. did nothing.

Trying to install in "Safe Graphics Mode" resulted in a freeze with  **only **the following message:
[FONT="Courier New"][COLOR="Navy"][   0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI[/COLOR][/FONT]

Again, pressing Enter, F1-F12, etc. did nothing.

Got the same "kernel panic" message when trying to load 6.06 (but I didn't record the exact codes).

Regarding the BIOS... A friend had suggested (prior to my installing more RAM) that I needed to upgrade the BIOS. I tried doing that, but was unsuccessful.

---

### Post by Seisen on 2007-06-06
I don't remember if Ubuntu asked for boot options when installing it, if it does put this in their

```
acpi=force
``` and see if that works.

---

### Post by ObscureReferenceMan on 2007-06-06
Does anyone think updating the BIOS might help?

---

### Post by ObscureReferenceMan on 2007-06-06
Just updated the BIOS! Trying installation again...

---

### Post by ObscureReferenceMan on 2007-06-06
Nope! Still get the same "kernel panic" message.

BTW, Seisen, I tried to access "Other Options", but couldn't find an ACPI option.

---

### Post by bone43 on 2007-06-06
> **ObscureReferenceMan said:**
> Nope! Still get the same "kernel panic" message.

BTW, Seisen, I tried to access "Other Options", but couldn't find an ACPI option.

Try this thread..

[http://ubuntuforums.org/showthread.php?t=422017:](http://ubuntuforums.org/showthread.php?t=422017:))

---

