---
title: "Checking laptop battery"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by oldcpu on 2007-05-28
What is the command to check on my laptop battery?

---

### Post by ramjet_1953 on 2007-05-28
Navigate to [COLOR="Blue"]System>Preferences>Power Management
[/COLOR]
When the window opens, click on the [COLOR="Blue"]General Tab[/COLOR]

In the [COLOR="Blue"]Notification Area[/COLOR] click on the [COLOR="Blue"]Always Display Icon button[/COLOR].

You will now have an icon always available in your top bar.

Just put the cursor over the icon and a bubble will open telling you of battery state.

Regards,
Roger :cool:

---

### Post by mcduck on 2007-05-28
If you still want a command, and your laptop has good ACPI support, 'acpi -V' works nice.

'sensors' is the other one, but it only works if you have lmsensors installed & configured (which often is not an easy task).

---

### Post by Kobalt on 2007-05-28
You can also find useful info with ```
cat /proc/acpi/battery/BAT0/info
```

---

