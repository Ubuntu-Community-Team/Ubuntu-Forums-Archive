---
title: "nearly black screen upon wake-up from sleep"
date: 2010-07-12
forum: Apple Hardware Users
---

### Post by zeroti on 2010-07-12
I was noticing that my screen was black (well the back-light was off but I could tell that that there was very dim color) whenever I would wake up from sleep. Since I have the option set to enter a password, I couldn't use the brightness keys to adjust the brightness and see what I was doing.

The solution was to put the following in /etc/pm/power.d/10_backlight_max
```

#!/bin/sh

fblevel 15

```

15 is the max brightness for my screen, but fblevel supports numbers up to 30.

---

