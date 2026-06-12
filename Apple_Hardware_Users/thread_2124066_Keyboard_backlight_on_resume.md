---
title: "Keyboard backlight on resume"
date: 2013-03-09
forum: Apple Hardware Users
---

### Post by Kopkins on 2013-03-09
I have ```

echo '5' > /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness
echo '25' > /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness

```

in rc.local to automatically adjust screen brightness and keyboard backlight on boot. 

And I have ```
#!/bin/bash
case "$1" in
thaw|resume)
echo '25' > /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness
;;
*)
;;
esac
exit $?
```

in /etc/pm/sleep.d/kbd_brightness

This works if sometimes if I manually click suspend, but if I close my laptop to make it suspend, on resume the keyboard is all the way bright again.

I just want my keyboard to not be all the way on all the time. 

Kopkins

---

### Post by Kopkins on 2013-03-14
How does anyone else manage keyboard brightness?

---

