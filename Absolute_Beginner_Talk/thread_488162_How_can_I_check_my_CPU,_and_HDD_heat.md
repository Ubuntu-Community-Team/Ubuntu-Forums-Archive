---
title: "How can I check my CPU, and HDD heat?"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Usta_AsH on 2007-06-29
Hello When I'm using windows I used to use SpeedFan. And That program shows your computer heat. How can I look my computer heat from where?

---

### Post by glennric on 2007-06-29
For cpu temp right click on your main panel and select Add to Panel.  Scroll down and look for the computer temperature monitor.  You can also look into the lm-sensors program for more temp info.  For hd temp look into the smartmontools package.  There is a simpler program but I can't remember it.

---

### Post by p_quarles on 2007-06-29
Another option, if you don't need to constantly monitor heat, is to open a terminal and type ```
acpi -t
```

That will give you the current CPU temperature in degrees Celsius. Don't know about hard drives, though.

---

### Post by Usta_AsH on 2007-06-30
> **p_quarles said:**
> Another option, if you don't need to constantly monitor heat, is to open a terminal and type ```
acpi -t
```

That will give you the current CPU temperature in degrees Celsius. Don't know about hard drives, though.

No support for device type: thermal

---

### Post by scxtt on 2007-06-30
install lm-sensors (or lm_sensors, can't remember what the ubuntu package is called) ... then run **sudo sensors-detect** and do what it tells you ... then load the module it says it needs ... type **sensors -f** ...

---

