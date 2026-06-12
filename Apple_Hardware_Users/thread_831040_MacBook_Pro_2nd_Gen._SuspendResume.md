---
title: "MacBook Pro 2nd Gen. Suspend/Resume"
date: 2008-06-16
forum: Apple Hardware Users
---

### Post by cvasilak on 2008-06-16
Hi there,

I am using Hardy on a 2nd Generation MacBook Pro C2D and the suspend/resume works flawlessly!. There are only two minor glitches and if anyone knows sth about them I would be grateful.

1) How can I programmatically set the backlight of the screen. I mean when I resume the backlight of the screen is set to 240 whereas when I suspend is set to 222. I have compiled and set up the backlight program which enables me to programmatically with a command set the brightness e.g. /usr/local/bin/backlight 222. How can I insert this command to be executed when the machine resumes from suspend?

2) Unfortunately the brightness keys and the keyboard backlight keys don't work when I resume, whereas they work before the suspend. However the volume keys work in both cases.

Thanks in advance for any answers...

Regards,
Christos

---

### Post by cyberdork33 on 2008-06-16
> **cvasilak said:**
> 1) How can I programmatically set the backlight of the screen. I mean when I resume the backlight of the screen is set to 240 whereas when I suspend is set to 222. I have compiled and set up the backlight program which enables me to programmatically with a command set the brightness e.g. /usr/local/bin/backlight 222. How can I insert this command to be executed when the machine resumes from suspend?

2) Unfortunately the brightness keys and the keyboard backlight keys don't work when I resume, whereas they work before the suspend. However the volume keys work in both cases.

1. I think you can add it to /etc/default/acpi-support

2. This is likely due to the pommed module needing to be reloaded. This should be able to be done from within the above file.

---

