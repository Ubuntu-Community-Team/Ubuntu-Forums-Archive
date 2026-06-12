---
title: "How to modify shutdown/reboot/etc buttons?"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Bluecircle on 2007-06-12
I have a custom script for hibernate and suspend that I'd like to replace the standard command with when I click hibernate or suspend on the shutdown menu. Where can I modify this?

---

### Post by Bluecircle on 2007-06-12
Ok is it the files in /usr/lib/hal/scripts/linux/ that I need to edit?

---

### Post by Bluecircle on 2007-06-12
brian@brian-laptop:~$ /sbin/s2ram --force
fgconsole: getconsolefd: Invalid argument
Switching from vt-1 to vt1
chvt: VT_ACTIVATE: Bad file descriptor
VT_WAITACTIVE: Bad file descriptor
**/sys/power/state does not exist; what kind of ninja mutant machine is this?**

hahahahahha

---

### Post by Bluecircle on 2007-06-12
Ok, I was right, just edit the files in /usr/lib/hal/scripts/linux/ to modify the commands in the shutdown menu.

Thanks for the help! ;)

---

### Post by srt4play on 2007-06-12
Yeah, what kind of ninja mutant machine do you have?

/sys/power/state exists on my IBM X40 laptop, but dpkg -S returns the file not found so I don't know what package provides it. I would guess one of the acpi packages.

EDIT:  hey cool thanks for sharing your solution.

---

### Post by Bluecircle on 2007-06-12
I have /sys/power/, but not /sys/power/state/. I don't know what's up with that but suspend is working perfectly now so no worries.

---

