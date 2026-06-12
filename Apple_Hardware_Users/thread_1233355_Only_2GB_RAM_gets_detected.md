---
title: "Only 2GB RAM gets detected"
date: 2009-08-06
forum: Apple Hardware Users
---

### Post by shivathreya on 2009-08-06
I have a MacbookPro5,5 with 4GB RAM. However, in Jaunty with kernel 2.6.28-15 only 2.8 GB is getting detected

See the respective outputs.

shiva@shiva-laptop:/var/cache/apt/archives$ free -b
             total       used       free     shared    buffers     cached
Mem:    2880790528 2405621760  475168768          0  100155392 1740005376
-/+ buffers/cache:  565460992 2315329536
Swap:            0          0          0

DMESG OUTPUT 

[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1907MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80


PLEASE HELP!

Shiva

---

### Post by tiagobt on 2009-08-06
Are you using the 64-bit version of Ubuntu? The 32-bit version can't handle more than 2 GB of RAM.

---

### Post by shivathreya on 2009-08-07
Thank you. I was so silly putting this question. Now its resolved.

Shiva

---

