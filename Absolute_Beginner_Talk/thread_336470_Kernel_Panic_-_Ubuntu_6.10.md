---
title: "Kernel Panic - Ubuntu 6.10"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by neologicial on 2007-01-11
Hey,
 have used Ubuntu on other pcs and it has worked fine and i love it!!!

I am running a...
                         
CPU: Intel(R) Celeron(R) D CPU 3.20GHz @ 3.19GHz - 0% Load
OS: Microsoft Windows XP Professional - 5.1.2600
Memory: Free: 125MB | Used: 323MB | Total: 447MB
Hard disk C:\ Free: 47.8GB | Used: 27GB | Total: 74.52GB
Display: 1024x768 @ 60 on Default Monitor and VIA/S3G UniChrome Pro IGP

And i have the latest ubuntu live cd. :KS  

i am trying to boot into the live cd so i can install it on aanother 30GB hard drive and the last thing it says is this//// [IMG]http://img504.imageshack.us/img504/7614/kernelpanicpz7.jpg[/IMG]


can you help??? i really need this asap because ubuntu is the best

Thanks ur all brilliant

---

### Post by Enverex on 2007-01-11
Try adding "noapic nolapic pci=routeirq acpi=off" minus the quotes to the end of your kernel boot line and see if that helps.

---

