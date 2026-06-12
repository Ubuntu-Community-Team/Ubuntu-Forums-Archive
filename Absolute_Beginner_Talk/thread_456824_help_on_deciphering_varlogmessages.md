---
title: "help on deciphering /var/log/messages"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by melquiades on 2007-05-28
I've looked at /var/log/messages on many occasions whenever I was sorting problems
on my Dapper system, and at times it has helped me. But I still can't figure out what 
all those bracket enclosed numbers on every entry for a kernel message means, like these

May 28 15:27:02 lappy kernel: **[17179571.376000]** USB1 USB2 USB3 USB4 USB7 LANC MODM 
May 28 15:27:02 lappy kernel: **[17179571.376000]** ACPI: (supports S0 S3 S4 S5)
May 28 15:27:02 lappy kernel: **[17179571.376000]** Freeing unused kernel memory: 288k freed
May 28 15:27:02 lappy kernel: **[17179571.428000]** vga16fb: mapped to 0xc00a0000
May 28 15:27:02 lappy kernel: **[17179571.560000]** Console: switching to colour frame buffer device 80x25


I've been looking for answers in the forum and the net but being a linux newbie 
I still can't find any satisfying answers ( or that I just don't know where to look ). If anyone 
could just tell me what these figures mean, or at least point where to start looking, then 
I'll start sleeping better at night. :D

TIA

---

### Post by Stephen Howard on 2007-05-28
I think its time in seconds (and milliseconds to the right of the decimal place).  If I'm right, then that error was generated around 198.8 days since the last reboot.

Of course, I could be wrong...

---

