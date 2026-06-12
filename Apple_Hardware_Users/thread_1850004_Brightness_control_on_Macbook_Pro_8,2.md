---
title: "Brightness control on Macbook Pro 8,2"
date: 2011-09-25
forum: Apple Hardware Users
---

### Post by proycon on 2011-09-25
Did anybody manage to get the brightness control working on a Macbook Pro 8,2 or 8,3 (AMD Radeon HD 6470M) ?

The slider moves when pressing the usual keys, but brightness is not changed. When I try manually using $ sudo echo "1" > /sys/class/backlight/acpi_video0/brightness  , the value and thus the brightness also remains unchanged. Compiling the latest pommed from git didn't help either.

Any ideas?

---

