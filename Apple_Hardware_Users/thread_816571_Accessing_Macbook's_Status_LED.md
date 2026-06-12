---
title: "Accessing Macbook's Status LED"
date: 2008-06-02
forum: Apple Hardware Users
---

### Post by mrc_001 on 2008-06-02
I am currently trying to find a way to use the status LED (the white one in the front next to the IR receiver) of my Macbook from the last generation before Santa Rosa. OS: Ubuntu 8.04 amd64; Linux 2.6.24-16-generic from the repository.

Normally, LED control files are situated in /sys/class/leds or somewhere in /proc/acpi (according to what I found on the internet and in the Linux documentation), but /sys/class/leds doesn't even exist. After loading the applesmc kernel module this directory is created, but without content.

The LED itself is not broken or something, it glows like usual when closing the lid.

Thanks for your help in advance.

-- Chris

---

